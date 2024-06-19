# Deadlocks
import numpy as np

def deadlock_erkennung(gesamten_ressourcen, zugewiesene_ressourcen, angeforderte_ressourcen)

#Deadlock Erkennung mittels der Banker-Algoritmus

#Zur einfacheren Handhabung in Numpy-Arrays konvertieren
gesamten_ressourcen = np.array(gesamten_ressourcen)
zugewiesene_ressourcen = np.array(zugewiesene_ressourcen)
angeforderte_ressourcen = np.array(angeforderte_ressourcen)


#schritt 1
Work = R - A.sum(axis=0)
Finish = np.array([False] * A.shape[0])

while True:
    found_process = False
    for i in range (len(Finish)):
        if not Finish[i] and np.all(C[i] <= Work):



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


