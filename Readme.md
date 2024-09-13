# Metropolis Algorithm Project

## Overview
This project implements the **Metropolis Algorithm** (also known as the **Simulated Annealing Algorithm**) to model and solve an optimization problem. The task involves arranging students from different classes into a grid of exam tables, with the objective of ensuring that students from the same class are either not seated next to each other (in the case of **Separation**) or are seated close together (in the case of **Stratification**).

The project was developed as part of the **Stochastic Modeling** course (API0074) during the Autumn semester of 2023 at **Université de Technologie de Compiègne**.

## Authors
- **SUN Hudie**
- **LAI Jinxing**

## Supervisor
- **Nikolaos Limnios**

## Date
September 13, 2024

## Problem Description
We are tasked with arranging 400 students from four different courses (RO05, SY01, MT21, GE27) into a 20x20 seating grid for an exam. The goal is to either **minimize** (**Separation**) or **maximize** (**Stratification**) the number of adjacent students who belong to the same course.

## Separation

### Configuration
1. **Initial Setup**:
   - The grid consists of 20 rows and 20 columns, with a total of 400 seats.
   - Each course is assigned a certain number of students (RO05: 50, SY01: 100, MT21: 150, GE27: 100).
   - A random initial configuration is generated, placing students into the grid.
   - The energy of the system is calculated based on the number of adjacent students from the same course.

### Energy Calculation
- The energy is defined as the sum of adjacent students belonging to the same course.
- The **Metropolis Algorithm** attempts to minimize this energy by swapping the positions of students and evaluating the resulting energy.

### Method: Metropolis Algorithm
The **Metropolis Algorithm** was implemented to minimize the energy of the system:
1. Calculate the current energy $ U_n $ of the system.
2. Randomly select two positions, swap them, and calculate the new energy $ U'_n $.
3. Compute the energy difference $ \Delta U = U'_n - U_n $.
4. If $ \Delta U < 0 $, the swap is accepted.
5. If $ \Delta U \geq 0 $, the swap is accepted with a probability of $ e^{-\Delta U / \text{temp}} $, where `temp` is the temperature parameter that controls the system's ability to escape local minima.

#### Key Results:
- After 10,000 iterations with a temperature of 0.1, the system’s energy reduced significantly, demonstrating the effectiveness of the algorithm.

## Stratification

In the **Stratification** phase, we modify the way energy is calculated. Unlike the **Separation** phase, where the energy increases if neighboring students belong to the same course, in **Stratification**, the energy increases when neighboring students belong to different courses.

#### Key Results:
- After 716,100 iterations with a temperature of 1.0, the algorithm successfully organized the students into a well-structured seating arrangement, where students from the same course were grouped together.

## Conclusion
The **Metropolis Algorithm** proved effective in optimizing seating arrangements. For simpler problems, a low-temperature approach yielded optimal results quickly. However, for more complex problems, starting with a high initial temperature and gradually lowering it (simulated annealing) was more effective.

This project demonstrated the potential of these stochastic algorithms in solving a range of optimization problems beyond classroom seating, with applications in various fields.

