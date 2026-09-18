# Compte rendu
## TP 1
### 4.2
#### Taille de l'image
L'image fait 2.01GB

#### 1
Le nom de l'image est **tp-api**
Son tag est **tp1**

### 5.2
#### 2
`proxy_pass` peut désigner l'hote car api est le nom du service docker

#### 3
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

