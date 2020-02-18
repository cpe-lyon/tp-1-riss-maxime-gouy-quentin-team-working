Manuel

1. A l’aide du manuel, identifiez le rôle de la commande which
*man which : permets de localiser une commande*

2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher
le terme option dans la page de manuel de which ?
*/command ex: /option*

3. Comment quitte-t-on le manuel ?
*q*

4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la
première page de la section 6 ; de quoi parle cette section ?
*man 6 intro*



Navigation dans l’arborescence des fichiers

1. allez dans le dossier /var/log
*cd /var/log*

2. remontez dans le dossier parent (/var) en utilisant un chemin relatif
*cd ..*

3. retournez dans le dossier personnel
*cd ~*

4. revenez au dossier précédent (/var) sans utiliser de chemin
*cd -*

5. essayez d’accéder au dossier /root ; que se passe-t-il ?
*Permission denied car nous n'avons pas les droits root pour accéder à ce dossier*

6. essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez
*Command not found*
*sudo ne marche qu'avec les applications*

7. à partir de votre dossier personnel, créez l’arborescence suivante :
*Mkdir Dossier1 → cd Dossier1 → touch Dossier1/Fichier1*
*Mkdir Dossier2 → cd Dossier2 → Mkdir Dossier2.1 Dossier2.2 → cd Dossier2.2 → touch Fichier2 Fichier3 *

8. revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis
Dossier1 ; que se passe-t-il ?
*rm (Chemin/NomDeFichier) ex : rm Dossier1/Fichier1*

9. quelle commande permet de supprimer un dossier ?
*rm -d Dossier1*

10. que se passe-t-il quand on applique cette commande à Dossier2 ?
*Le dossier n'étant pas EMPTY, impossible de supprimer*

11. comment supprimer en une seule commande Dossier2 et son contenu ?
*rm -r Dossier2*



Commandes importantes


1. Quelle commande permet d’afficher l’heure ? A quoi sert la commande time ?
*date*
*affiche le temps d'exécution d'une commande*

2. Dans votre dossier personnel, tapez successivement les commandes ls puis la ; que peut-on en déduire
sur les fichiers commençant par un point ?
*ls affiche les dossiers alors que la affiche les fichiers commençant par un point*
*c'est juste des fichiers appart (souvent config ou dossier de fichier de config)*

3. Où se situe le programme ls ?
*which ls : /usr/bin/ls*

4. Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande ? Utilisez les commandes alias ou alias pour en savoir plus sur la nature de cette commande.
*elle affiche les droits des fichiers, celui qui a créé le fichier (ou du moins le responsable), la date de création, l'espace disque allouée*
*man ll : no manual entry*
*alias ll : ls -alF*

5. Quelle commande permet d’afficher les fichiers contenus dans le dossier /bin ?
*ls /bin*

6. Que fait la commande ls .. ?
*affiche la liste des fichiers du dossier parent dans lequel on se trouve*

7. Quelle commande donne le chemin complet du dossier courant ?
*pwd*

8. Que fait la commande echo 'yo' > plop exécutée 2 fois ?
* > : ça écrase le contenu  fichier pour écrire l'erreur ex : echo 'yo' > plop*

9. Que fait la commande echo 'yo' >> plop exécutée 2 fois ?
* > : ça fait un append à la fin du fichier pour écrire l'erreur ex : echo 'yo' > plop*

10. A quoi sert la commande file ? Essayez la sur des fichiers de types différents.
*détermine le type de fichier (l'extension)*

11. Créez un fichier toto qui contient la chaîne Hello Toto ! ; créer ensuite un lien titi vers ce fichier
avec la commande ln toto titi. Modifiez à présent le contenu de toto et affichez le contenu de titi :
qu’observe-t-on ? Supprimez le fichier toto ; quelle conséquence cela a-t-il sur titi ?
* on est capable de lire le fichier toto avec le lien titi*
*Aucune on est capable de lire quand même le contenu avec titi*


12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le
contenu de titi ; quelle conséquence pour tutu ? Et inversement ? Supprimez le fichier titi ; quelle
conséquence cela a-t-il sur tutu ?
*on lie les deux fichiers. Une modification sur l'un entraine une modification sur l'autre*
*tutu : no such file or directory , le lien n'existe plus, mais ça ne supprime pas tutu*
*tutu contient seulement le nom du fichier sur lequel il a fait un lien*

13. Affichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et
reprendre le défilement à l’écran ?
*CTRL + S    CTRL + Q*

14. Affichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les
lignes 10 à 20.
*head -N Fichier avec N nombre de ligne*
*tail -N Fichier avec N nombre de ligne*
*awk 'NR==10,NR==20' /var/log/syslog*

15. Que fait la commande dmesg | less ?
*afficher le tampon des message des noyaux less ça permet d'afficher page par page le fichier*

16. Affichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet d’afficher la page
de manuel de ce fichier ?
*affiche la listes des comptes utilisateurs *
*man 5 passwd -> pour l'aide*

17. Affichez seulement la première colonne triée par ordre alphabétique inverse
*cut -c1 /etc/passwd | sort -r*

18. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seulement les utilisateurs connectés) ?
*wc -l /etc/passwd*

19. Combien de pages de manuel comportent le mot-clé conversion dans leur description ?
*man -k conversion | wc -l*
*-> 4*

20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine
*find / -name "passwd"*

21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier
~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null
*find / -name "passwd" > ~/list_passwd_files.txt 2>/dev/null*

22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu
précédemment
*cat .bashrc | grep ll* 

23. Utilisez la commande locate pour trouver le fichier history.log.
*sudo apt install mlocate*
*locate history.log*
*/var/log/apt/history.log*

24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?
*touch fichierTest*
*locate fichierTest*
*Il n'apparait pas car il n'est pas contenu dans la base de données des fichiers indéxés (fonction locate)*




Nano est un éditeur de texte rudimentaire, où toutes les commandes évidemment se font au clavier.
 Les raccourcis clavier les plus courants sont affichés en bas de l’écran, mais sous une forme peut-être
inhabituelle :
• ^G signifie Ctrl + G
• M-U signifie Alt + U
 Quelques raccourcis utiles :
F1 ou Ctrl + G Affichage de l’aide
Ctrl + X Quitter nano / Fermer une fenêtre / Exécuter une commande
Ctrl + R Ouvrir un fichier
Ctrl + O Enregistrer sous
Ctrl + S Enregistrer
Ctrl + K Couper
Ctrl + U Coller
Ctrl + W Rechercher
Ctrl + \ Remplacer
Ctrl + C Afficher des informations sur la position du curseur (numéro de ligne, de colonne)
Alt + U Annuler
Alt + E Refaire
1. Copiez le fichier /var/log/syslog dans votre dossier personnel sous le nom log.txt, puis ouvrez-le avec
nano
*cp /var/log/syslog log.txt*
*nano log.txt*

2. Remplacez toutes les occurrences du mot kernel par le mot noyau


Without nano 
	sed -i 's/searched_word/replaced_word/g' filename
	sed -i 's/kernel/noyaux/g' log.txt
With nano 
Alt + R
entrer your search word
enter your replacement word
Press A to replace all instances

3. Déplacer les 10 premières lignes à la fin du fichier

3)Select lines with alt + up arrow
    Cut with Ctrl + K
    Go to end of file with Ctrl + _ and Ctrl + V
    Paste with Ctrl + U
    
4. Annulez cette action

Alt + U

5. Enregistrez le fichier avant de quitter nano

 Ctrl + X
    Yes to save the buffer and set the filename 
    or
    Ctrl + O / Ctrl + S


Exercice 4 

1) *cp .bashrc .bashrc_bak*

2) *nano .bashrc*
    *Ctrl W*
    *Enter force_color_prompt=yes*
*decommente*

3) *source .bashrc to test*

4)
*PS1 = '${debian_chroot:+($debian_chroot)}\[\033[01;31m\][\A] - \[\033[01;32m\]\u@\h\[\033\[00m\]:\[033[01;36m\]\w\[\033[00m\]\$'*