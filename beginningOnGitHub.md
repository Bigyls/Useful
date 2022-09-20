

# Initier un projet.

----

### Vous n'avez encore rien fait dans votre projet.

```bash
git init mon_projet
```

Cela va créér un répertoire "mon_projet" dans le dossier courant.

### Vous avec déjà débuté votre projet.

Votre répertoire "mon_projet" existe donc déjà, et il contient déjà des fichiers. Placez vous dans votre répertoire et exécutez la commande suivante:

```bash
git init
```

### Ajoutez des fichiers à votre git.

Votre répertoire contient des fichiers, il faut les ajouter à git pour qu'il puisse tenir compte de ces fichiers.

```bash
git add my_file
```

Ou si plusieurs fichiers:

```bash
git add my_file1 my_file2
```

Ou pour ajouter tous les fichiers du répertoire:

```bash
git add .
```

### Afficher le statut de votre git.

```bash
git status
```

Vous obtiendrez ainsi la liste des fichiers non encore ajoutés à votre git, et la liste des fichiers déjà ajoutés, mais n'ayant pas encore été mis a jour dans votre git depuis leur dernière modification.

### Faire un commit (prise d'une photo/snapshot).

Vous avez modifié un fichier (par exemple my_file1), il faut alors faire un commit pour que git enregistre ces modifications:

```bash
git commit my_file1 -m "ajout de la fonction md2html"
```

L'argument -m permet d'ajouter un bref commentaire décrivant votre modification. Ce commentaire est obligatoire; si vous n'ajoutez pas l'argument -m et son commentaire, l'éditeur nano s'ouvrira alors pour que vous puissiez ajouter votre commentaire.

Il est aussi possible de commit tout le projet 

```bash
git commit -m "ajout de la fonction md2html"
```

### Obtenir une liste de tous vos commit et de leurs commentaires.

```bash
git log
```

Pour chaque commit, la première ligne correspond au sha du commit.

### Revenir à un ancien commit.

Il faut faire un `git log` pour connaitre son sha.

```bash
git checkout sha_du _vieux_commit
```

Pour revenir au dernier commit (le plus récent):

```bash
git checkout master
```

### Créér une branche.

Vous voulez faire une modification sur l'un de vos fichiers tout en conservant votre dernier commit intacte; il faut pour cela créér une branche.

```bash
git branch nom_de_la_branche
```

Pour savoir dans quelle branche vous vous situez:

```bash
git branch
```

Vous verrez alors vos differentes branches: la branche master (c'est la branche principale), et votre nouvelle branche. L'astérix devant master signifie que vous êtes toujours dans la branche master. Il faut alors changer de branche avant de faire vos modifications:

```bash
git checkout nom_de_la_branche
```

Pour créér une branche en se plaçant directement dans celle ci:

```bash
git checkout -b nom_de_la_branche
```

### Merger une branche avec le master.

Les modifications apportées dans la branche vous conviennent. Il faut alors fusionner votre branche et votre master. Placer vous dans la branche master:

```bash
git checkout master
```

Puis :

```bash
git merge nom_de_la_branche
```

Pour effacer la branche devenue inutile:

```bash
git branch -D nom_de_la_branche
```

### Cloner un repository ou un gist

```bash
git clone path_du_repository_ou_du_gist path_du_repertoire_a_creer_en_local
```

### Push vers github

Relier votre git local à votre repository github (à faire une seule fois):

Créer un repository sur votre compte github, puis placez vous dans votre dossier local contenant votre git et votre projet local. Puis entrez la commande suivante:

```bash
git remote add origin https://github.com/nomutilisateur/MonProjet.git
```

Faire un push (pensez à faire un commit avant !)

```bash
git push
```

Ou:

```bash
git push --set-upstream origin master
```

Il faudra alors entrez votre nom d’utilisateur et mot de passe sauf si vous avez installé un certificat ssh

Sinon, il vous faudra installer gh et le lancer avec les commandes suivante:

```bash
sudo apt install gh
gh auth login
```

Il faudra alors selctionner les options GitHub.com => HTTPS => Yes => Paste ann authentication token (token créer dans Settings => Developer settings => Personnal acces tokens => Generate token (avec tous les droits et pas d'expiration))

Ainsi, vous pouvez faire n'importe quelles actions sans rentrer d'identifiants.

### Push vers gist

- Créer un gist depuis votre compte github.
- Clonez votre gist en local
- Placer votre fichier dans votre git local

Faire ensuite un commit puis un git push:

```bash
git push git@gist.github.com:<votre gist id e4.....>.git
```

### Pull de github vers votre repo local

Pour récupérer les dernières modifications de votre repository distant (sur github) vers votre repository local:

Placez vous dans votre repository local

```bash
git pull origin master
```

### Activer l'authentification par SSH

Créer une paire de clés SSH:

```bash
ssh-keygen -t ed25519 -C "<email>@<email>"
```

Récupérer votre clé public:

```bash
ls ~/.ssh
config  id_rsa  id_rsa.pub  known_hosts

cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3Nza.....
```

Ajouter votre clé public en vous connectant sur github et en allant dans les menus 'settings' puis 'SSH and GPG keys'

Activer l'authentification SSH dans un repo existant:

```bash
git remote set-url origin git@github.com:<user name>/<repo name or gist id>.git
```


