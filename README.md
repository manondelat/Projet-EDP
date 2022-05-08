# Projet-EDP

LoadVTX() renvoie sous la forme d’un tableau les coordonnées de chaque nœud du maillage.

LoadELT() renvoie deux tableaux.  Le premier tableau représente les triangles (les éléments) du maillage. Le deuxième renvoie k=0 ou 1 en fonction de si l’élément appartient à Omega_0 ou Omega_1.

PlotSubDomain() réalise un affichage graphique du maillage.

l.71: les variables vtx, elt et label sont les sorties des fonctions pour le maillage 1. Pour avoir les résultats du code sur le maillage 2, on met un # devant les lignes 71,72 et 73. On enlève ensuite les # devant les lignes 76,77,78


Boundary() renvoie sous la forme d’un tableau toutes les arrêtes du bord.

matadj() renvoie la matrice d’adjacence. 

Ccmpt() renvoie pour chaque élément un numéro qui indique à quel ensemble connexe il appartient. 

InnerBoundary() renvoie, grâce à la fonction Ccmpt(), uniquement les arrêtes du bord intérieur. 

verification_InnerB() réalise un affichage graphique de InnerBoundary. Cela nous permet de vérifier que InnerBoundary  renvoie bien les arrêtes du bord intérieur.  Pour effectuer la vérification, on enlève le # devant "verification_innerB(elt)" l.196.

PlotMesh()  va nous permettre d’afficher des fonctions sur le maillage.


sol_exacte() nous renvoie la solution exacte qui est égale à 1 sur tout Omega. Cela nous permet d’afficher (l.204) notre solution exacte sur le maillage.




Nous allons ensuite nous atteler à la construction des matrices du problème variationnel


aire_triangle() renvoie l’aire de l’élément e mis en argument.

Kloc() renvoie la matrice de rigidité locale 

Rig()  renvoie la matrice de rigidité globale

Mloc() renvoie la matrice de masse locale en 2D

Mass_Omega2()  renvoie la matrice de masse globale sur Omega2.

l.322 : On fait une liste de tous les éléments de Omega2. Cela nous permet grâce à la fonction aire_omega2 (l.330), de calculer l’aire de Omega2 en additionnant l’aire de tous ses éléments. Ensuite, la fonction test_mass_omega2() (l.339) nous permet d’effectuer le test de vérification de la matrice de masse sur Omega2.  Les deux fonctions aire_omega2 et test_mass_omega2 sont égales: il est probable que la matrice de masse sur Omega2 soit bien définie. Pour lancer les fonctions, il suffit d'enlever le # devant "print(aire_omega2(vtx,elt) " l.336 et devant "print(test_mass_omega2(vtx,elt))" l.343.

Mloc1D() est la matrice de masse locale sur les arrêtes.

Massbord() renvoie la matrice de masse sur le bord de Omega_0 (InnerB).

Test_Massbord() renvoie  le chiffre 2 qui correspond bien à la longueur du bord intérieur. Il est donc probable que notre matrice Massbord soit bien définie. Pour le vérifier, il suffit d'enlever le # devant "print(Test_Massbord(vtx,InnerB)) ".

a() renvoie le membre de gauche du système linéaire que l’on souhaite résoudre.


l.410 : F_final() renvoie le membre de droite du système linéaire que l’on souhaite résoudre, en additionnant F() et F2()

l.414 : sol est la solution du système linéaire
l.415 : on trace la solution approchée de la question 5. Si on la print, on a un vecteur avec que des 1. Cela est de bonne augure car la solution que l’on cherche est égale à 1.

l.426 : uex_lagrange() renvoie les valeurs de la solution exacte pour chaque nœud du maillage.

l.432 : diff renvoie la différence entre la solution approchée sol et uex_lagrange. Nous allons représenter cette erreur graphiquement grâce à la fonction Plotmesh().  On voit que l’erreur est de l’ordre de 10^{-15}, ce qui est négligeable. 


l.440 : L2  représente la norme L2 de la différence entre la solution exacte et la solution approchée. Elle est égale à environ 6.64x10^{-31} pour le maillage 1 et à 4.97 x 10^{-30} pour le maillage2. Cela est négligeable. La norme L2 serait théoriquement encore plus faible si on affinait le maillage.


Nous allons ensuite nous atteler à la résolution du deuxième problème (question 7)

l.446 : Mass()  renvoie la matrice de masse sur tout Omega. 

l.462 : sol2 renvoie la résolution du nouveau système linéaire correspondant au problème de la question 7. On affiche ensuite  la solution approchée à l’aide de PlotMesh.

