
## 🔧 Features

- ✅ Automatically filters and processes customer orders based on eligibility
- ✅ Assigns optimal plant-port pairs to minimize total cost
- ✅ Visualizes plant-port logistics network
- ✅ Displays manufacturing cost and product distribution across plants
- ✅ Annotates cost distribution by plant using real order data
- ✅ Exports final optimized assignments to CSV (optional)

---

## 📊 Data Inputs

The model reads from an Excel file with the following sheets:

| Sheet Name        | Description                                                  |
|------------------|--------------------------------------------------------------|
| `OrderList`       | List of customer orders (Order ID, Product ID, Customer, etc.) |
| `ProductsPerPlant`| Maps product IDs to eligible plant codes                     |
| `PlantPorts`      | Maps plants to their connected shipping ports                |
| `VmiCustomers`    | Lists customers assigned to specific plants (VMI restriction)|
| `FreightRates`    | Raw freight costs by port used to compute average freight    |
| `WhCosts`         | Manufacturing cost per unit at each plant                    |

---

## 🧠 Optimization Logic

The optimization model works as follows:

1. **Eligibility Mapping**  
   - Filter plants by product compatibility  
   - Enforce VMI restrictions (customer-plant fixed mapping)  
   - Identify valid ports per plant

2. **Cost Calculation**  
   - Combine warehouse cost + average freight per port  
   - Calculate total cost for all valid (Plant, Port) pairs

3. **Assignment**  
   - Choose the combination with **minimum total cost** per order  
   - Discard infeasible orders with no valid combinations

---

## 📈 Visualizations

- 🌐 **Plant-Port Network Graph** (Plotly + NetworkX)
- 📊 **Manufacturing Cost per Plant** (Seaborn)
- 📦 **Number of Products per Plant**
- 💰 **Total Cost Distribution by Plant with $ annotations**

---

## 🗂️ Example Output

| Order ID     | Plant Code | Port   | Total Cost |
|--------------|------------|--------|-------------|
| 1447126331   | PLANT03    | PORT04 | $2.45       |
| 1447133115   | PLANT02    | PORT03 | $10.45      |
| ...          | ...        | ...    | ...         |

---

## 🚀 How to Run

1. Clone this repo:
   ```bash
   git clone https://github.com/yourusername/supply-chain-optimizer.git
   cd supply-chain-optimizer
