    import numpy as np

    def deadlock_erkennung(gesamten_ressourcen, zugewiesene_ressourcen, angeforderte_ressourcen):  
    # Deadlock Erkennung mittels der Banker-Algoritmus

    # Zur einfacheren Handhabung in Numpy-Arrays konvertieren
    gesamten_ressourcen = np.array(gesamten_ressourcen)  
    zugewiesene_ressourcen = np.array(zugewiesene_ressourcen)  
    angeforderte_ressourcen = np.array(angeforderte_ressourcen)

    # Überprüfen ob die Matrizen die richtige Form haben
    num_process = len(zugewiesene_ressourcen)  
    num_resources = len(gesamten_ressourcen)
    
    # Schritt 1: Berechnung des verfügbaren Work-Vektors 
    work = gesamten_ressourcen - zugewiesene_ressourcen.sum(axis=0)  
    finish = np.array([False] * num_process)  

    # Schritt 2: Suche nach einem Prozess, der ausgeführt werden kann  
    while True:
        found_process = False
        for i in range(num_process):
            if not finish[i] and np.all(angeforderte_ressourcen[i] <= work):  

                # Schritt 3: Markiere diesen Prozess als beendet  
                finish[i] = True  
                # Gebe seine Ressourcen frei
                work += zugewiesene_ressourcen[i]  
                found_process = True
                break

        # Schritt 4: Überprüfen, ob alle Prozesse beendet sind  
        if not found_process:  
            break  

    if np.all(finish):
        return False # Kein Deadlock gefunden  
    else:
        return True # Deadlock gefunden  

    # Funktion zur Eingabe einer Matrix
    def eingabe_matrix(prompt, num_process, num_resources):
        print(prompt)
        matrix = []
        for i in range(num_process):
            row = input(f"Zeile {i + 1} (durch Leerzeichen getrennte Werte): ")
            matrix.append(list(map(int, row.split())))
        return matrix

    # Funktion zur Eingabe eines Vektors
    def eingabe_vektor(prompt):
        return list(map(int, input(prompt).split()))

    # Eingabe der Anzahl an Prozessen
    num_process  = int(input("Bitte geben sie die Anzahl der Prozesse an:"))
    num_resources  = int(input("Bitte geben sie die Anzahl der ressourcen an:"))

    # Eingabe des ressourcen-vektors
    gesamten_ressourcen = eingabe_vektor("Bitte geben sie den ressourcenvektor (durch leerzeichen getrennt) ein:")

    # Eingabe der Belegungsmatrix
    zugewiesene_ressourcen = eingabe_matrix("Bitte geben Sie die Belegungsmatrix ein:", num_process, num_resources)

    # Eingabe der Anforderungsmatrix
    angeforderte_ressourcen = eingabe_matrix("Bitte geben Sie die Anforderungsmatrix ein:", num_process, num_resources)

    # Berechnung des initialen Ressourcenrestvektors
    initialer_ressourcenrestvektor = np.array(gesamten_ressourcen) - np.array(zugewiesene_ressourcen).sum(axis=0)

    # Ausgabe der eingelesenen und berechneten Daten
    print("\nRessourcen (interaktiv eingegeben):")
    print(gesamten_ressourcen)
    print("\nBelegungsmatrix (vom Simulator berechnet):")
    print(zugewiesene_ressourcen)
    print("\nAnforderungsmatrix (vom Simulator berechnet):")
    print(angeforderte_ressourcen)
    print("\nInitialer Ressourcenrestvektor (berechnet):")
    print(initialer_ressourcenrestvektor)

    # Deadlock erkennung basierend auf eingebenen Daten 
    if deadlock_erkennung(gesamten_ressourcen, zugewiesene_ressourcen, angeforderte_ressourcen): 
        print("Deadlock gefunden!")  
    else:  
        print("Kein Deadlock gefunden.")  
