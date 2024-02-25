import numpy as np
import matplotlib.pyplot as plt

def logistic_equation(N, r):
    return (r + 1) * N - r * N**2

def simulate_population_growth(N0, r, num_time_steps):
    population = np.zeros(num_time_steps + 1)
    population[0] = N0
    
    for t in range(num_time_steps):
        population[t + 1] = logistic_equation(population[t], r)
    
    return population

# Poblaciones iniciales
N0_values = [0.043, 0.23, 1.5, 2.8]

# Parámetro r
r_value = 2.9

# Número de pasos de tiempo
num_time_steps = 20

# Simulación y gráfica para r = 2.9
plt.figure(figsize=(8, 6))

for N0 in N0_values:
    population = simulate_population_growth(N0, r_value, num_time_steps)
    plt.plot(population[:-2], population[2:], label=f'N0 = {N0}')

plt.title(f'Evolución de la población (r = {r_value})')
plt.xlabel('Nt')
plt.ylabel('Nt+2')
plt.legend()
plt.show()
