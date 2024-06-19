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

    #Interaktive Eingabe des Ressourcenvektors
    ressourcen_input = input("Bitte geben Sie den Ressourcenvektor durch Leerzeichen getrennt ein: ")
    ressourcen = list(map(int, ressourcen_input.split()))
    
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

# Beispiel Daten für Vektoren und Matrizen  
R = [10, 5, 7]
A = [
    [0, 1, 0],
    [2, 0, 0],
    [3, 0, 2],
    [2, 1, 1],
    [0, 0, 2]
]
C = [
    [7, 4, 3],  
    [1, 2, 2],  
    [6, 0, 0], 
    [0, 1, 1],  
    [4, 3, 1]  
]

if deadlock_erkennung(R, A, C): 
    print("Deadlock detected!")  
else:  
    print("No deadlock detected.")  

