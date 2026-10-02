# Compte rendu
## TP 1
### 4.2
#### Taille de l'image
L'image fait 2.01GB

#### 1
Le nom de l'image est **tp-api**
Son tag est **tp1**

### 5.2
#### 1
`proxy_pass` peut désigner l'hote car api est le nom du service docker

#### 2
`try_files $uri $uri/ /index.html` sert a essayer la page de notre application puis a load la page par defaut (ici index.html) si rien n'est trouvé. Sans la ligne, l'application ne peut pas load de page il y a donc une erreur 404

### 5.3
L'image fait 63.4MB

## TP 2
### Etape 0
#### Taille des images du TP1
```Bash
tp-api:mesure                    9e7ab79d4467       2.01GB             0B        
tp-front:tp1                     c39cff8be780       63.4MB             0B    
```

#### Durée d'une reconstruction complète (cache vidé)
**Backend :**
```Bash
real    0m25,439s
user    0m0,086s
sys     0m0,073s
```

**Frontend :**
```Bash
real    0m30,141s
user    0m0,098s
sys     0m0,086s
```

#### Durée d'une reconstruction après modification d'une ligne de code
**Backend :**
```Bash
real    0m0,457s
user    0m0,067s
sys     0m0,048s
```

**Frontend :**
```Bash
real    0m31,778s
user    0m0,093s
sys     0m0,093s
```

#### Sous quel utilisateur tourne l'API ?
**Backend :**
```Bash
uid=0(root) gid=0(root) groups=0(root)
```

**Frontend :**
```Bash
uid=0(root) gid=0(root) groups=0(root),0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),11(floppy),20(dialout),26(tape),27(video)
```

### Etape 3.7
La commande `time docker build --no-cache -t tp-api:tp2 .` donne le resultat suivant :
```Bash
real    0m41,192s
user    0m0,199s
sys     0m0,073s
```

La commande `docker images | grep tp-api` donne le resultat suivant :
```Bash
tp-api:tp2                     18dd684c3530        288MB             0B        
```

La commande `docker run --entrypoint id --rm tp-api:tp2` donne le resultat suivant :
```Bash
uid=1654(app) gid=1654(app) groups=1654(app)
```


La commande `time docker build -t tp-api:tp2 .` apres modification d'un caractere de Program.cs donne le resultat suivant :
```Bash
real    0m8,398s
user    0m0,069s
sys     0m0,056s
```

### Etape 3.8
La commande `time docker build --no-cache -t tp-api:tp2 .` donne le resultat suivant :
```Bash
real    0m34,990s
user    0m0,145s
sys     0m0,073s
```

La commande `docker images | grep tp-api` donne le resultat suivant :
```Bash
tp-api:tp2                     0e814712f872       63.4MB             0B        
```

La commande `time docker build -t tp-api:tp2 .` apres modification d'un caractere de tasks.ts donne le resultat suivant :
```Bash
real    0m16,603s
user    0m0,110s
sys     0m0,062s
```

### Etape 5

Le job qui échoue est le job api, celui qui a l'assert modifié. Le job front s'execute quand meme.

Entre mon push et le temps ou je me suis rendu compte qu c'était cassé il c'est passé 15min

### Etape 6

**1 /** Le plus gros gain de taille c'est fait sur la partie backend, apres l'ajout du dockerfile multi-stage et du dockerignore. Le plus gros gain de temps c'est fait sur la partie frontend, pour la reconstruction du fichier apres modification d'une ligne de code. Ce ne sont pas les meme car les modifications apportées a l'un ne sont pas les meme que pour l'autre  
**2 /** Pour réduire ce temps, il faudrait détecter l'erreur plus tot.
**3 /** L'erreur de workflow que j'ai rencontré était sur le path du fichier de test du backend et du frontend, j'avais mis un mauvais chemin.  

## TP 3
### Etape 3.1
La configuration ESLint du projet contient 3 problemes, 2 erreurs et 1 warning

## Etape 3.3
Parmi les erreurs corrigées, deux d'entre elles concernait un mauvait type. Les varibles était déclarées en let alors qu'elle n'ont jamais de nouvelles variable. En revanche, le warning pouvait etre un bug potentiel car cela peut affecter la gestion et la correction des erreurs.

## Etape 4.3
La meilleur option dans notre cas serait l'option B. En effet, c'est peut etre la solution la moins correct sur le papier mais cela nous permet de ne pas bloquer sur des tests complexe a resoudre et couteux en temps. C'est la solution la plus rapide dans l'immediat

## Etape 5.2
`ignore-unfixed: true` est utile dans les deux cas. En developpement elle evite que l'on ai des erreurs insolubles. En production, cette ligne reste utile pour les gros projet car une erreur insoluble peut arriver dans certaines situation et le fait que cela bloque est tres problematique pour le bon fonctionnement du service

