# Deadlocks
import numpy as np

def deadlock_erkennung(gesamten_ressourcen, zugewiesene_ressourcen, angeforderte_ressourcen)

#Deadlock Erkennung mittels der Banker-Algoritmus

#Zur einfacheren Handhabung in Numpy-Arrays konvertieren
gesamten_ressourcen = np.array(gesamten_ressourcen)
zugewiesene_ressourcen = np.array(zugewiesene_ressourcen)
angeforderte_ressourcen = np.array(angeforderte_ressourcen)


#überprüfen ob matrixen richtige Form haben 
num


#schritt 1
Work = gesamten_ressourcen - zugewiesene_ressourcen.sum(axis = 0)
Finish = np.array([False] * num_process)


#schritt 2 Index für i => finsih[i] = false    angeforderte_ressourcen[i] <= work 
while True:
    found_process = False
    for i in range (num_process):
        if not Finish[i] and np.all(angeforderte_ressourcen[i] <= work):

#schritt 3 falls so ein prozess gefunden wurde, diesen als beendet markieren 
finish [i] = True   #seine ressourcen frei geben 

work += zugewiesene_ressourcen[i]
    found_process = True 
            break

#schritt 4 checken ob alle prozesse fertig sind 
if np.all(finish):
    return False #kein deadlock gefunden 
else:
    return True #deadlock gefunden




#beispiel Daten für vektoren und Matrixen 
R = [10, 5, 7]
A = [
    [0, 1, 0],
    [2, 0, 0],
    [3, 0 , 2],
    [2, 1 , 1],
    [0, 0, 2]
    ]
C = [
    [7, 4, 3]
    [1, 2, 2]
    [6, 0, 0]
    [0, 1, 1]
    [4, 3, 1]
  ]


if deadlock_erkennung(R, A, C)
    print("Deadlock detected!")
else 
    print("No deadlock detected.")


