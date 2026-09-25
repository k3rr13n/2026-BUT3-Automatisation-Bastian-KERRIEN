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
