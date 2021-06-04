# TP Broken Authentication

A travers ce TP, vous allez voir comment facilement usurper l'identité de quelqu'un grâce a ses informations personnelles ou bien grace à sa session.
Faites votre compte-rendu dans un document texte que vous nous enverrez par mail.

Disclaimer: à ne pas reproduire dans un cadre non-professionnel 👿

------------------  
Cloner le repo git :
```bash
git clone https://github.com/anthony-rlld/tp-broken-authentication.git
```

Lancer le serveur php en local   
```bash
cd tp-broken-authentication/sitesPhp
```  

```bash
php -S localhost:8092 (ou n'importe quel autre port si celui est déjà pris)
```

__Vous devrez utiliser ce serveur pour les deux exercices__   
------------------  
## Exercice 1 (14 points)

Marc Martin est votre collègue, vous savez qu'il possède un compte sur le site que vous venez d'installer ci-dessus. Vous allez ainsi essayer de vous y connecter avec une attaque bruteforce (password spraying).
Vous connaissez déjà son email, c'est : marc.martin@gmail.com.

Pour ce faire, vous n'allez pas utiliser une simple liste de mots de passes connus, mais vous allez en générer des plus personnalisés, grace à l'outil cupp.

### Prerequis: 
Vous devez avoir python installé, si jamais ce n'est pas le cas :

Sous linux/wsl :  
```bash
apt-get install python3
```

Sous window :  
https://www.python.org/ftp/python/3.9.5/python-3.9.5.exe

-----------------

Vous devez ensuite télécharger cupp:

```bash
git clone https://github.com/Mebus/cupp.git
```
```bash
cd cupp
```    

Maintenant, vous allez génerer des mots de passes possibles pour votre collègue Marc Martin, pour cela, vous allez avoir besoin d'informations personnelles le concernant.
Dans la réalité on peut chercher sur internet, dans notre cas, marc est un personnage fictif.

Marc (prénom) Martin (nom) travaille chez toyota, il est né le 04/06/1980 et à eu un enfant qui s'appelle Thomas avec sa femme laura.
Marc n'est pas complétement néophyte, il utilise des mots de passes assez long, avec bien souvent des majuscules, des chiffres ou encore des caractères spéciaux.
Rappelez vous que vous connaisez son adresse mail : marc.martin@gmail.com

### Question 1 (4 points)

Génerez une liste de mot de passes possibles à l'aide de cupp pour Marc Martin.

Pour lancer cupp :
`python3 cupp.py -i` ou `./cupp.py` (si python est dans votre path)   

### Question 2 (10 points)

Vous allez maintenant utiliser le logiciel HYDRA afin de faire une attaque par dictionnaire sur le site.
Trouvez le mot de passe de Marc, et connectez vous à son compte.

Pour ce faire vous devez installer hydra :
```bash
git clone https://github.com/vanhauser-thc/thc-hydra.git
```
```bash
cd thc-hydra
```
```bash
./configure
```
```bash
sudo make install
```

Pour ceux qui sont sous windows :

vous pouvez utilisez hydra pour windows ici : https://discord.com/channels/755329550220656681/841282879220744252/850306553515868191

Clonez le, executez le puis ouvrez un shell dans le dossier et vous pouvez y taper les commandes hydra.

Apparement hydra n'arrive pas a joindre votre serveur quand vous lancez avec php -S => utilsez WAMP plutot, cela a marché pour Esteban
Cupp mets des lignes vides entre chaque password => supprimez les sinon hydra ne trouvera pas le mot de passe

-----------

Tapez maintenant `hydra` pour le lancer, regardez les arguments nécessaires pour lancer une attaque bruteforce par dictionnaire sur un formulaire HTTP en POST.
Regardez à quoi ressemble le site php mis à disposition, sur quelle page il amène lors d'une erreur, quelle est la requête qu'il fait pour essayer de se connecter.

Vous pouvez cherchez des exemples sur internet si cela ne marche pas, on en trouve pas mal.
Pensez à remplacer `localhost` par `127.0.0.1`, et n'oubliez pas de préciser le port.

--------------------------------
## Exercice 2 (6 points)
Rendez-vous dans la partie session du site php mis à disposition.
Votre but est de trouvez deux manières différentes d'obtenir l'identifiant de session.
Bonne chance ! 👊
