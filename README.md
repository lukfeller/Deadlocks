# Deadlocks
import numpy as np

def deadlock_erkennung(R, A, C)

#Deadlock Erkennung mittels der Banker-Algoritmus
# R = Ressourcenvektor 
# B = Belegungsmatrix
# A = Anforderungsmatrix

R = np.array(R)
B = np.array(B)
A = np.array(A)
#Zur einfacheren Handhabung in Numpy-Arrays konvertieren

#beispiel Daten für vektoren und Matrixen 

R = [10, 5, 7]
A = [
    [0, 1, 0],
    [2, 0, 0],
    [3, 0 , 2],
    [2, 1 , 1],
    [0, 0, 2]
C = [
    [7, 4, 3]
    [1, 2, 2]
    [6, 0, 0]
    [0, 1, 1]
    [4, 3, 1]
  ]
  


