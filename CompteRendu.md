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
