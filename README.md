# Cloud-Cost-Optimizer
Cloud Cost Optimizer - Cloud Resource Allocation & Cost Optimization (MILP)
Constraint Optimization Problem (COP)

Problem Statement: My company (Calgon Carbon/Kuraray) deploys multiple applications and services across a cloud infrastructure across the globe. We need to minimize overall cost and ensure compliance with performance Service Level Agreements (SLAs). This requires selecting the optimal combination of Virtual Machine (VM) types, quantities, and regions, considering per-VM resource capacities, latency requirements, and region-specific pricing.
Solution: I developed a Python optimization model using PuLP to minimize cloud infrastructure cost across the U.S. and European regions. 
This application leverages a Mixed-Integer Linear Programming (MILP) model built in Python with PuLP to act as an intelligent cloud deployment planner. It automatically determines the optimal mix of server types and data center locations to run enterprise applications at the lowest possible cost. 
This is a tool that will help our company decide where to run its software and how big the servers should be by factoring in (simulated data for now, can be replaced with real data later) cost, speed, and sustainability. It takes in CPU, memory, and storage that each application needs, the cost of different cloud servers, company locations, performance limits (such as how far away servers can be, latency). I added in optional factors that we need to consider before deciding, including carbon emissions (sustainability is a big factor at my company in making business decisions now), license limits, and budgeting. The app uses optimization algorithms (PuLP in Python) to test millions of combinations to find the most efficient plan. 
This tool will cut cloud costs and improve performance. This tool will optimize and reduce total costs by (hopefully) ~25%.

Mathematical Model: 
1.	Decision Variables:
a.	How many of each server type to run (x[i,j,k])
b.	Which regions each app should run in (y[i,k])

2.	Constraints:
a.	Meet each app’s minimum CPU, memory, and storage requirements
b.	Stay within latency limits so users are not too far from servers
c.	Only use valid combinations of apps, regions, and server types
d.	Stay under a given monthly budget (if one is set)
e.	Meet high availability rules (certain apps must run in two or more regions)
f.	Uses Big M constraint to link binary and numerical values

3.	Goal:
a.	Compute cost: how much each virtual machine costs per hour

4.	Solver: use PuLP to test and compare possible combinations of servers and regions to find the single best option that minimizes cost while meeting each requirement. 

5.	Outputs:
a.	Which region to use for each app
b.	How many and what type of servers to deploy
c.	Total monthly cost and breakdown

