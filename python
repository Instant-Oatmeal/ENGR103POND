########################################################################################
# Program Filename: Homework # 6
# Author: Owen Lloyd
# Date: 5/2/2024
# Description: This code prints the settling velocity of different grain sizes in water. 
# This also prints the time it takes for each grain to settle to the bottom, Orifice size,
# and money saved by Corvallis Water.
# Input: This program inputs values such as sediment density, water densit, dynamic viscosity of the fluid, 
# sediment grain size, acceleration due to gravity, and particle Reynolds number. 
# Outputs: Settling Velocity, time it takes for each grain to settle to the bottom, Orifice size,
# and money saved by Corvallis Water.
########################################################################################

import numpy as np

grain_sizes = [10E-6,20E-6,30E-6,40E-6,50E-6,60E-6]
grain_velocities = []

#######################################################################
# Function: settling_velocities
# Description: plays a guessing game and solves for the settling velocity of each grain size 
# Parameters: grain_size_for_guess
# Return values: x (velocity in m/s)
# Pre-Conditions: x=1, dif_x=1
# Post-Conditions: x = velocity, dif_x=1
####################################################################### 

def settling_velocities(grain_size_for_guess):
  x = 1
  dif_x = 1
  while dif_x >= .000000001:
    guess = np.sqrt((4/3) * (1.65) * ((9.81 * grain_size_for_guess)/(1.4 + (36/((1000 * grain_size_for_guess * x)/1E-3)))))
    dif_x = abs(x-guess)
    x=guess
  return x

#######################################################################
# Function: time_to_settle
# Description: calculates amount of time (in hours) it takes for particle to hit the bottom
# Parameters: x
# Return values: t (in hours)
# Pre-Conditions: x = choosen grain velocity 
# Post-Conditions: t = time in hours 
####################################################################### 

def time_to_settle(x):
  t = 1/(grain_velocities[x] * (1800))
  return t 

#######################################################################
# Function: orifice_size
# Description: calculates size of orifice in meters
# Parameters: t
# Return values: d (in meters)
# Pre-Conditions: time
# Post-Conditions: d size of orifice in meters
####################################################################### 

def orifice_size(t):
  a = (4000/(t*.98)) * np.sqrt(2) * (np.sqrt(2/9.81))
  d = np.sqrt((4*a)/np.pi)
  return d


# Printing settling velocties for each grain size
print("Settling Velocity:")
for x in range(len(grain_sizes)):
  grain_velocities.append(settling_velocities(float(grain_sizes[x])))
  print(grain_sizes[x], "in meters = ", settling_velocities(float(grain_sizes[x])) , "m/s." )

# Printing the time that it takes for each grain size to reach the bottom of the pond
print("Time to settle in a 2 m depth pond:")
for x in range(len(grain_sizes)):
  print("For", grain_sizes[x], "grain size sediments it takes", time_to_settle(x) , "hours to settle in the pond." )

# Prints the orifice size needed from the amount of time that it takes to allow 85% of the sediments in the pond to settle before the water leaves the pond
print("The orifice needs to be " , orifice_size(1.030310752053341), "m in diameter to allow 85% of the sediments in the pond to settle before the water leaves the pond.")

# Prints the amount of money saved from the Corvallis Water Treatment plant
print("The energy savings of removing 10% of the water (or 400 million gallons) being processed unnecessarily by the Corvallis wastewater treatment plant is", (1875*.9) ,"twh and will save the city", (.116 * 1875000 * .9),"dollars per year.")
