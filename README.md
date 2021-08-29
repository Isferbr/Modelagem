# Modelagem
Simulação de Monte Carlo em Python

import numpy as np

def f(x): # função a ser integrada
  y = 1 + x**2
  return y

a = 5  # limite inferior do intervalo
b = 10 # limite superior do intervalo
N = 1000000 # número de interações
n = 0 # contagens entre a função e y = 0

x = a + (b - a)*np.random.uniform(size = N) # pontos aleatórios entre a e b
max_y = max([f(x[i]) for i in range(N)]) # encontrando o máximo da função no intervalo
y = max_y*np.random.uniform(size = N) # pontos aleatórios entre 0 e max_y

for i in range(N):
  if y[i] < f(x[i]):
    n+=1

# a área da integração em relação a área do retângulo segue a proporção n/N
A = max_y * (b - a) * (n / N)
