# AI-Based-Cloud-Resource-Auto-Scaling-System

This project deploys an **AI-driven cloud resource auto-scheduler** designed to predict server CPU usage on a cloud environment and dynamically adjust resource allocation. Using a predictive model trained on both historical and real-time data, the system forecasts CPU usage in 1-minute intervals, providing a 10-minute sliding window prediction. This approach enables proactive scaling of resources, optimizing cloud costs and system efficiency.

The solution leverages Docker images for both the server and AI model, which are hosted on Docker Hub and deployed in real-time according to AI predictions. This deployment operates in a local Kubernetes cluster within a virtualized environment, with future compatibility for production-grade clusters.

## Project Workflow
1. **AI Model Deployment**: The AI model analyzes CPU usage data, producing future predictions at set intervals (configurable for training time and prediction window).
2. **Dynamic Scaling**: Based on the model's predictions, the system triggers scale-up or scale-down actions to optimize resource utilization.
3. **Local Kubernetes Deployment**: The server and AI model run in Docker containers within a Kubernetes cluster hosted locally via Minikube, allowing for seamless management and orchestration.

## Setup Instructions

### Prerequisites
- **Docker Engine** or **Docker Desktop**
- **Minikube** and **kubectl** for Kubernetes
- Required Python packages (specified in `requirements.txt`)

### Steps

1. **Start Docker Engine**  
   Ensure Docker Engine or Docker Desktop is running.

2. **Start Kubernetes Cluster**  
   Initialize Minikube and verify nodes:
   ```bash
   minikube start
   kubectl get nodes

3. **Deploy Kubernetes Resources**
   Apply deployment and service configurations:
   ```bash
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml

4. **Install Python Dependencies**
   Install all required packages:
   ```bash
   pip install -r requirements.txt

5. **Run AI Model and Visualization**
   Execute the AI model and scaling program:
   ```bash
   python main2.py

6. **Run Server and Automated Client (Optional)**
   To run the server.py, start the service that handles requests.
   Use automateclient.py to simulate real-time client requests to the server for testing purposes.
   ```bash
   python server.py
   python automateclient.py
  The automated client simulates a real-time environment by sending requests to the server, but it’s optional and intended only for testing.

## File Descriptions
1. **main2.py**: Runs the core AI model, generating CPU usage predictions and triggering scaling operations in real-time.
2. **Graph.py**: Generates graphical representations of predicted CPU usage, helping visualize resource demand trends.
3. **server.py**: A simple cloud server service that simulates client requests (customizable as per specific client requirements).
4. **automateclient.py**: Simulates real-time client requests to the server for testing purposes (optional).
