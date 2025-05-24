# Kubernetes MostAllocated Scheduler on Azure AKS

This project demonstrates how to deploy a **custom Kubernetes scheduler** using the `MostAllocated` strategy on **Azure Kubernetes Service (AKS)**. It overrides the default scheduling behavior to prioritize nodes with higher resource utilization, optimizing workload packing and potentially reducing costs.

## 🚀 Purpose

- Replace the default Kubernetes scheduler with one using the **MostAllocated** strategy.
- Improve resource efficiency in AKS by packing pods onto nodes with higher utilization.
- Learn how to configure a custom scheduler, permissions, and testing strategy.

## 🔧 Key Features

- Custom scheduler configuration using `NodeResourcesFit` with `MostAllocated` scoring.
- Role-based access control (RBAC) setup for secure scheduler deployment.
- Configurable deployment and multi-replica scheduler for HA testing.
- Sample pod deployment to validate the custom scheduler behavior.

## 📁 Project Structure

- `custom-scheduler-config.yaml`: ConfigMap with the scheduler configuration.
- `custom-scheduler-deployment.yaml`: Deployment manifest for the custom scheduler.
- `rbac.yaml`: Complete RBAC setup (ServiceAccount, RoleBindings, ClusterRoleBindings).
- `test-deployment.yaml`: A test pod using the `custom-scheduler`.

## 📦 Technologies

- Kubernetes (v1.31+)
- Azure AKS
- MostAllocated Scheduling Strategy

## 🛠️ How It Works

1. **Scheduler Configuration:**
   - Uses `NodeResourcesFit` plugin with `MostAllocated` strategy.
   - Prioritizes memory (weight 2) over CPU (weight 1) for scheduling decisions.

2. **Deployment:**
   - Deploys `kube-scheduler` image with the custom configuration.
   - Mounts config from ConfigMap.

3. **RBAC:**
   - ServiceAccount `my-scheduler` with all necessary ClusterRoleBindings.
   - Permissions for volume scheduling and leader election leases.
