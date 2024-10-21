## On a 3 agents A1 , A2 , A3 et un tableau T d'entiers : |0|3|4|7|8|10|6|5|
A1 envoie tout le tableau T au agents A2et A3
A2 recois le tableau et calcul le nombre d'elements pairs 
A3 recois le tableau et calcul le nombre d'elemnts impaires 
A2 envoie nb elem pairs a A1
A3 envoir le nombre d'elem impairs a A1

## CLASSIFIYING THE FONCTIONS OF EACH AGENT 
Agent A1:
Initializes the integer array T and sends it to both agents A2 and A3.
Receives the results from A2 (number of even elements) and A3 (number of odd elements).

Agent A2:
Receives the array T from A1.
Calculates the number of even elements in T.
Sends the result back to A1.

Agent A3:
Receives the array T from A1.
Calculates the number of odd elements in T.
Sends the result back to A1.
