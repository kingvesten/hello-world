# Z-Casino

import random
import math

print("Welcome to Z-Casino\n")
name = input("Quel est ton nom ? ")
bitcoin = 200
f1 = 0
print(str(name)+".\nTu possede "+str(bitcoin)+" Bitcoin.")

while bitcoin>0:#Boucle Generale du Jeu.
    while True: #Boucle pour la Mise + verification de la mise + Try / Catch ValueError.
        try:
            mise = int(input("Combien veux-tu miser ? tu as "+str(bitcoin)+" Bitcoin."))
            if mise <= 0 or mise > bitcoin:
                print("Tu m'arnaque !")
                mise = 0
                continue
            else:
                bitcoin = bitcoin - mise
                break
        except ValueError:
            print("\nError 404.")
            continue
    while True: #Boucle choix du nombre de l'utilisateur + verification + try / catch ValueError.
        try:
            choix = int(input("Choisi un Nombre ( 1 - 50 ) : "))
            if choix <= 0 or choix > 50:
                print("Error 404. ( 1 - 50 )")
                continue
            else:
                break
        except ValueError:
            print("\nError 404.")
            continue
    nbm = random.randint(1,51)
    if nbm % 2 == 0: #modulo sur le NomBreMagic pour savoir s'il est pair/impaire + initialiser / incrementer NOIR ou ROUGE
        #print("Noir.")
        noir = 1
        rouge = 0
    else: #modulo sur le NomBreMagic pour savoir s'il est pair/impaire + initialiser / incrementer NOIR ou ROUGE
        #print("Rouge.") 
        rouge = 1
        noir = 0
    
    if noir == 1: #Print le Numero + la couleur du NomBreMagic.
        print("La roulette c'est arreter sur le numero ==== "+str(nbm)+" Noir ====")
    else:
        print("La roulette c'est arreter sur le numero ==== "+str(nbm)+" Rouge ====")

    if choix % 2 == 0: #Modulo sur le Choix pour afficher Noir ou Rouge.
        noir = noir + 1
        print("Tu avais choisi le Numero "+str(choix)+" Noir")
    else:
        rouge = rouge + 1
        print("Tu avais choisi le Numero "+str(choix)+" Rouge")
    
    if nbm == choix:
        print("\n\n\nTu as Gagner 3 fois ta mise car tu as eu le meme nombre que la Roulette. Felicitation.\n")
        bitcoin = bitcoin + mise * 3
        print("Tu possede "+str(bitcoin)+" Bitcoin.")
    elif noir == 2 or rouge == 2:
        print("\n\n\nTu n'as pas gagner. Mais tu as trouver la bonne couleur donc je te rends 50% de ta mise. Better Luck Next Time.\n")
        bitcoin = bitcoin + mise / 2
        print("Tu possede "+str(bitcoin)+" Bitcoin.")
    else:
        print("Tu n'as pas trouver le bon nombre n'y la bonne couleur. Too Bad.\n") 
        print("Tu possede "+str(bitcoin)+" Bitcoin.")

    while True:
        try:
            rp = str(input("Veux-tu rejouer ?\n"))
            if rp == "oui":
                break
            elif rp == "non":
                f1 = 1
                break
            else:
                print("Error 404 ( oui - non )")
                continue

        except ValueError:
            print("Error 404.")
            continue
    
    if f1 == 1:
        print("\n\n\n"+str(name)+" Tu repars avec - "+str(bitcoin)+" - Bitcoin\n\nMerci d'avoir Jouer.")
        break

    if bitcoin == 0:
        print("Tu n'as plu d'argent. du balais..!\n")
