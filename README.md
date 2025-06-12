# Vehicle Routing Problem (VRP): Solving with Adaptive Simulated Annealing

This project addresses the **Vehicle Routing Problem (VRP)** using **Adaptive Simulated Annealing (ASA)** to efficiently determine optimal routes for multiple vehicles serving a set of customers with specific demands. Each vehicle starts from a depot and must respect capacity constraints while minimizing the total distance traveled.

---

## 🚚 Problem Overview

The **Vehicle Routing Problem (VRP)** involves:
- Assigning customers to vehicles
- Optimizing visiting orders
- Respecting vehicle capacities
- Minimizing total travel distance

This problem is critical in logistics, transportation, and supply chain optimization.

---

## 🧠 Solution Architecture

### 1. Data Processing
- Extract vehicle and customer data (coordinates, demands, capacities)
- Organize data for fast and efficient access

### 2. Initial Solution Construction
- Uses a **Greedy-Best Insertion** heuristic:
  - Customers sorted by distance from depots (farthest first)
  - Each customer is tested in all possible positions in each route
  - Chooses position with the lowest increase in route cost
  - Ensures vehicle capacity constraints are respected

### 3. Adaptive Simulated Annealing (ASA)
- Iteratively explores neighborhoods of the current solution
- Uses **adaptive temperature control** to guide the search
- Supports **reheating** to escape local minima

### 4. Visualization
- Graphical representations of:
  - Route layouts
  - Cost convergence over time

---

## 🧱 Data Structures

### Vehicle Data
- Capacities and depots stored in lists for rapid access

### Customer Data
- Coordinates and demands managed in structured arrays/lists

### Distance Matrix
- Euclidean distance precomputed between all points (depot + customers)

---

## 🔄 Solution Representation

### Routes
- Represented as lists of customer indices per vehicle

### Evaluation
- Computes total route distance
- Checks each vehicle route for capacity feasibility

---

## 🔁 Neighborhood Operations in ASA

| Operation      | Description                                                       | Probability |
|----------------|-------------------------------------------------------------------|-------------|
| **Swap**       | Exchange customers between two routes                             | 20%         |
| **Relocate**   | Move a customer from one route to another                         | 30%         |
| **2-opt**      | Reverse a segment within a single route                           | 25%         |
| **Cross-exchange** | Swap segments of routes between two vehicles                 | 15%         |
| **Or-opt**     | Move a short sequence of customers to a different route position  | 10%         |

---

## 🌡️ Adaptive Temperature Control

### Adaptive Cooling Rate
- **Slows down** cooling when improvements are found
- **Speeds up** cooling when no improvements occur
- Bounded between `alpha_start` and `alpha_end`

### Reheating Mechanism
- If no improvement for 20+ iterations:
  - **Temperature is increased ×10**
  - Resets the improvement counter
  - Helps escape deep local optima

---

## 📊 Visualization Features
- Route plotting to visually analyze solutions
- Convergence graphs to monitor cost improvement over iterations

---

## 🛠️ Technologies Used
- Python (for algorithm implementation)
- Matplotlib / Plotly (for visualization)
- NumPy / SciPy (for numerical operations)

---
