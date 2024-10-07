import random

def calculer_prix(age):
    prix_base = 150
    if age <= 3:
        return 0  # Billet gratuit
    elif age >= 65:
        rabais = random.randint(15, 55)  # Rabais aléatoire
        prix = prix_base * (1 - rabais / 100)
        return prix, rabais
    else:
        return prix_base, None

def reservation():
    total_global = 0
    while True:
        print("######################################")
        print("IFT-1004 Airlines")
        print("######################################")
        print("La meilleure compagnie aérienne au monde!")
        
        # Combien de billets ?
        nb_billets = int(input("Combien de billets souhaitez-vous réserver ? "))
        total_client = 0
        
        for i in range(1, nb_billets + 1):
            print(f"============\nPassager {i}/{nb_billets}\n============")
            nom = input("Nom du passager : ")
            age = int(input("Âge du passager : "))
            
            prix, rabais = calculer_prix(age)
            if rabais is not None:
                print(f"Rabais appliqué pour {nom} : {rabais}%")
            print(f"Prix du billet réservé pour {nom} : {prix:.2f}$")
            total_client += prix
        
        # Afficher le total pour ce client
        print(f"Montant total à encaisser pour cette réservation : {total_client:.2f}$")
        total_global += total_client
        
        # Menu : continuer ou quitter
        while True:  # Ajout d'une boucle pour vérifier la validité du choix
            choix = input("1. Enregistrer un autre client\n2. Quitter\nEntrez votre choix : ")
            if choix == "1":
                break  # Continuer avec un autre client
            elif choix == "2":
                print(f"Montant total cumulé pour tous les clients enregistrés : {total_global:.2f}$")
                print("Bye bye!")
                return  # Quitter le programme
            else:
                print("Choix invalide. Veuillez entrer 1 ou 2.")  # Instruction 11

reservation()
