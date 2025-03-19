**Deploying a Scalable Python Web App on Azure App Service**

**Project Overview**
This project demonstrates how to deploy a scalable Flask web application using Azure App Service. The application is hosted on Azure, allowing it to handle multiple user requests efficiently without manual infrastructure management. The goal is to leverage Azure's cloud capabilities to deploy and manage a web application seamlessly.

**Technologies Used**
Azure App Service – To host and manage the Flask application
Flask – A lightweight Python web framework
Git – For version control and deployment
Bash – Used for executing commands in Azure Cloud Shell

**1. Setting Up the Flask Application Locally**

**1.1. Setting Up a Local Python Application**
I created a new folder for the project:
mkdir my-scalable-flask-app && cd my-scalable-flask-app

Initialized a new Git repository:
git init

Created a virtual environment and installed Flask:
python3 -m venv venv source venv/bin/activate pip install flask

**1.2. Creating the Flask Application**
I created a new directory for my project and initialized the Flask application with a simple app.py file.
nano app.py

Inside app.py, I added the following basic Flask code:
from flask import Flask  app = Flask(__name__)  @app.route('/') def home(): return "Hello, Azure! This is my Flask App."  if __name__ == '__main__': app.run(host='0.0.0.0', port=8080)

**1.3. Creating a Virtual Environment and Installing Dependencies**
Since Azure requires a requirements.txt file to install dependencies, I created a virtual environment and installed Flask.
python3 -m venv venv source venv/bin/activate pip install flask pip freeze > requirements.txt

**1.4. Testing the Flask App Locally**
Before deploying, I tested the application locally.
python app.py

The application started running on http://0.0.0.0:8080. If the port was already in use, I stopped the conflicting process or changed the port.

**2. Deploying to Azure App Service**

**2.1. Deploying Using Azure Portal**
I created the web app named hari-flask-app inside the flask-app-group resource group using Azure Portal. This provided an environment to host and manage my Flask application.

**2.2. Connecting Local Project to Azure App Service**
After setting up my Flask application, I initialized a Git repository and connected it to Azure’s deployment source.
git init git add . git commit -m "Initial commit" git remote add azure <Azure Git Remote URL>

**2.3. Pushing Code to Azure**
git push azure master

**Decision-Making and Issues Faced:**
Initially, I encountered an issue: fatal: Could not read from remote repository. I fixed this by verifying the correct remote URL and ensuring I had the necessary access permissions.
Another issue was Git asking for a password when pushing the code. To resolve this, I checked my authentication settings and ensured I was using the correct credentials.

**3. Configuring and Monitoring the Deployment**
Once the deployment was complete, I accessed the Azure Portal to verify the application status, check logs, and configure settings such as scaling options.
I also tested the web application’s functionality using the Azure-provided URL:
echo "https://hari-flask-app.azurewebsites.net"
This confirmed that the app was running successfully on Azure.

**4. Key Learnings and Challenges**

**4.1. Understanding Cloud Deployment**
Deploying a Flask app on Azure provided hands-on experience with cloud-based hosting and infrastructure management.

**4.2. Overcoming Git Authentication Issues**
I faced authentication problems while pushing to Azure. I resolved these by configuring the correct credentials and access permissions.

**4.3. Testing and Debugging in a Cloud Environment**
Testing a locally running Flask app is different from debugging an application on a cloud platform. Understanding how to monitor and troubleshoot deployment issues in Azure was a key learning.

**5. Conclusion**
This project helped me understand how to deploy and manage a Flask web application on Azure App Service. It reinforced my knowledge of Flask, Git, and cloud deployment while providing practical experience in handling real-world deployment challenges.
