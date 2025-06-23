Serverless Flask App Deployment using AWS ECS + ECR + Fargate
This project demonstrates how to containerize a simple Flask web application, push it to Amazon Elastic Container Registry (ECR), and deploy it using Amazon ECS with Fargate launch type.
🚀 Tech Stack
- Python (Flask)
- Docker
- Amazon ECR
- Amazon ECS + Fargate
- IAM
- EC2 (Ubuntu)
- CloudWatch
🧠 What I Learned
- Writing a production-ready Dockerfile
- Pushing Docker images to Amazon ECR
- Creating ECS Task Definitions and Clusters
- Deploying a container using Fargate (serverless)
- Debugging service failures using CloudWatch
- IAM permissions and ECS service roles
📁 Project Structure
my-ecs-app/
├── app.py         # Simple Flask app with one route
├── Dockerfile     # Instructions to containerize the app
└── README.md      # Project documentation
⚙️ Setup Steps
Step 1: Clone Repository
git clone https://github.com/your-username/aws-ecs-fargate-flask-app.git
cd aws-ecs-fargate-flask-app
Step 2: Dockerize the Flask App
docker build -t flask-ecs-app .
Step 3: Push to Amazon ECR
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <your-ecr-url>
docker tag flask-ecs-app:latest <your-ecr-url>:latest
docker push <your-ecr-url>:latest
Step 4: Deploy with ECS (Fargate)
- Go to Amazon ECS → Create Cluster (Networking only)
- Create Task Definition → Fargate → Add container (use ECR image URL)
- Deploy a Service in the cluster
- Set public load balancer or assign public IP
✅ Output
When deployment is successful, visiting the load balancer/public IP will show:
Hello from ECS + ECR + Fargate!
📌 Notes
- Make sure security groups allow inbound traffic on port 80.
- ECS task role must have permissions for ECR and logs.
- Use CloudWatch logs to troubleshoot if app doesn't load.
👨‍💻 Author
Thatiparthi Saishiva
Email: thatiparthisaishiva@gmail.com
📎 License
This project is open-source and free to use for learning purposes.
