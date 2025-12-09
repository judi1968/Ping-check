# 1 .Creation des classes et des fonctions de base
## Class :
* **TypePion** (id *int*, nom *string*)
    * id = 1 : Roi
    * id = 2 : Reine
    * id = 3 : Fou
    * id = 4 : Chevalier
    * id = 5 : Sisiny
* **Pion** (id *int*, type *TypePion*, vie *double*)
* **Barre** (id *int*, width *double* , height *double* , x *double* , y *double*)
* **Ballon** (width *double* , height *double* , x *double* , y *double*)
* **Table** (width *double* , height *double*)
* **Joueur** (id *int*, nom *string*, pions *Pion[ ]*)

## Fonction :
* ### VerifyKingDead 
    **class :** Pion
    **argument :** none
    **return :** Boolean
    **etapes :**
    * verification si this.TypePion.id est 1 (Roi)
    * oui : verifie si **this.vie est 0**
        * oui : **return true**
        * non : **return false**
    * non : **return false**
* ### vieDimininue 
    **class :** Pion
    **argument :** none
    **return :** (return true *resy* or false *jeux continue*) 
    **etapes :** 
    * this.vie - 1
    * appel fonction verifie si le roi est mort **VerifyKingDead**
        * oui : **return true**
        * non : **return false**

# 2 . Creation de l'interface de configuration du serveur
* ## Page 1 : 
    * **Title :** Ajout nombre de pion (2, 4, 6, 8)
    * **Affichage :** Creer un formulaire qui entre le nombre de pion
        * Input type number
        * button valider
    * **Traitement :** Quand bouton clicker, on prend le nombre et on verifie si le nombre est ( 2 ou 4 ou 6 ou 8) : 
        * oui : on cree deux joueur avec les nombres de pions la dedant :    
            * 2 : Pion 2 devant, derriere :  Roi 1 , Reine 1
            * 4 : Pion 4 devant, derriere : Fou 1,  Roi 1 , Reine 1 , Fou 1 
            * 6 : Pion 6 devant, derriere : Chevalier 1 Fou 1,  Roi 1 , Reine 1 , Fou 1 , Chevalier 1
            * 8 : Pion 8 devant, derriere : Sisiny 1, Chevalier 1 Fou 1,  Roi 1 , Reine 1 , Fou 1 , Chevalier 1 , Sisiny 1
        * non : on affiche l'erreur dans le formulaire que le nombre de pion est invalide
    entrer dans la page **Page 2**

* ## Page 2 :
    * **Title :** Ajout de vie pour chaque pion
    * **Affichage :** Creer un formulaire qui entre le nombre de vie pour chaque pion
        * boucle du pion du chaque joueur et Input type number (libelle nom du joueur et nom du pion )
        * button valider
    * **Traitement :** Quand bouton clicker, on prend les nombres de vies et on nombre et on verifie si le nombre est negative : 
        * oui : on affiche un exception
        * non : on le met dans le vie du pion du joueur
    Si tout sera mieux , creer le socket multi thread qui attend deux joueur et ensuite **Page 3**

* ## Page 3 :
    * **Title :** Attend les joueurs ou affiche le joueur (IP , nom)
    * **Affichage 1:** Attend les joueurs
    * **Affichage 2:** Affiche le joueur avec leurs vie

# 3 . Creation du client qui repond au serveur 
* Run le client
* creer l'interface du client
    * ajout terrain
    * ajout pion (avec image et nombre de vie)
    * ajout bar
    * ajout ballon
* mouvement du ballon en reseau 
* collision entre le ballon et le bar
* collision entre le ballon et le pion
* pion fait l'appel au fonction vieDiminue quand le ballon est en collision avec lui
* affichage du jeux terminer (texte) quand le roi est mort