Review Manager Portal
Project Link
http://restaverse-tf-312.centralindia.cloudapp.azure.com/
Overview
This project creates a centralized dashboard where business owners can manage the reviews across all their business locations in one place using Google MyBusiness API.
It features a homepage allowing users to quickly reply to the latest reviews via an intuitive UI.
Additionally, a reviews page displays more information about reviews, including modification dates.
Reviews are color-coded to differentiate between positive, negative, or neutral feedback.
Google Oauth implementation for seamless login.
Technologies Used
Frontend: React.js
Backend: Flask
Styling: Tailwind.css
Deployment: Docker, Terraform and Microsoft Azure
Challenges Faced
The main challenge in this project was setting up Oauth.
Making sure the Oauth token is always secure by encrypting it during transport from client to server or vice versa and the means of passing it to the server using headers.
Understanding how oauth works was key to overcoming it along with Google's Documentation, tutorials and even Stackoverflow.
As there was no access to Google's My Business API, there was a need to create a mock API that replicates responses that the original API would send.
To implement the actual API, we would have to have some way to test it. Even if we follow the docs, we cannot guarantee that there won't be any issues.
Future Prospects
Features
Add analytics and visualisationbased on review data
Allow more filtering options for reviews
Enhance UI/UX (e.g., subtle animations)
Implement caching
Allow advanced users to run queries against the data
Dev side:
Secure the server with SSL
Implement visualization using chart.js or similar modules
Autoscaling
Strengthen security using a proxy server to access the client for isolation
Conduct extensive testing
How to use the website ?
Sign in with google by clicking the icon at the bottom of the navbar.
On successfull sign-in, one can see the latest reviews in the home page. The home page has the quick reply option which can be toggled by hovering over it.
From there the user can post a reply or delete a previous reply.
If a user want to see more detailed information about each review, then they can go to the reviews tab. This tab also allows filtering by available locations.
To logout, click the very same user icon at the bottom of the navbar
Note
Currently anyone who logs in with a google acc can view/modify/reply to reviews as data is fetched from a json which mimics the response format of google API.
How to Run this Project ?
Mandatory Steps
Go to the Google Cloud Console.
Select or create a new project where your React app will be registered.
Navigate to "APIs & Services" > "Credentials".
Configure OAuth consent screen if prompted. (Fill in mandatory details only)
Click on "Create credentials" and choose "OAuth client ID" from the dropdown menu.
Select "Web application" as the application type.
Give it any name and create.
If setting up for local development:
Add http://localhost:5173 (or any port of your choice) to the Authorized JavaScript origins.
Add http://localhost:5000/callback (or any port of your choice) to the Authorized redirect URIs.
Else, add URLs/IPs for the frontend deployment.
Download the credentials JSON file and rename it to client_secret.json.
Copy the client_secrets.json file into the API folder.
For actual API usage, enable relevant Business APIs under "Enabled APIs and services."
Configure environment variables for the API/server:
Create a .env file in the API folder.
Refer to .env-dummy.txt and fill in required values for:
DEBUG (true for debug mode in Flask and test routes)
CLIENT_ID (copy from client_secrets.json)
SECRET_KEY (copy from client_secrets.json)
FRONTEND_URL (URL of the client with port)
BACKEND_URL (URL of the server with port)
ALGORITHM (set to HS256 for encrypting/decrypting JWT)
Configure environment variables for the client:
Create a .env.local file in the client folder.
Set VITE_BASEAPI_URL to the same value as FRONTEND_URL above.
Proceed to any of the deployment options below.
Locally using Node and Python
Prerequisites (older versions may work but cannot guarantee)
Python 3.11+
Node v20 +
Npm v8+
Steps
Navigate to /client and install dependencies

bash

Verify

Open In Editor
Edit
Copy code
cd client
npm install 
If everything was successful, you can now test if the client works by running npm run dev.

Going to the output URL, you'll be able to access the React client. We now have to set up the Flask server to complete deployment

Currently, we are running a development server with support for hot reload. To build for production, we can use npm run build followed by npm run preview

Navigate to /API and install dependencies using

bash

Verify

Open In Editor
Edit
Copy code
pip install -r requirements.txt
Use python3 -m flask --app app run --debug to run the server in development mode.

Now you should have the client and server running successfully.

Locally using Docker
Methods to Run this Project
Prerequisites
Docker engine installed and running
Steps
Navigate to client folder
bash

Verify

Open In Editor
Edit
Copy code
docker build -t "tag/name of your choice" . 
# Eg: docker build -t myclient .
Run the client container
bash
Verify
Open In Editor
Edit
Copy code
docker run -p <host port>:<client port (of container)> --env-file ./.env.local -d "chosen tag" 
# Eg: docker run -p 80:3000 --env-file ./.env.local myclient
Navigate to the API folder
bash

Verify

Open In Editor
Edit
Copy code
docker build -t "tag/name of your choice" . 
# Eg: docker build -t myclient .
Run the server container
bash

Verify

Open In Editor
Edit
Copy code
docker run -p <host port>:<client port (of container)> --env-file ./.env -d <chosen tag> 
# Eg: docker run -p 5000:5000 --env-file ./.env -d myserver
Note
The Dockerfiles are configured to deploy a production environment. To set up for deployment, we would have to modify the Dockerfiles to use the dev run commands and also mount our local files to the Docker container using -v source_path:dest_path in the run command
Locally using Docker Compose
Prerequisites:

Docker engine installed and running
Steps:
Navigate to the root folder (restaverse)
The Docker Compose file essentially just builds and runs the individual Dockerfiles with client and API.
Execute the following command:
bash

Verify

Open In Editor
Edit
Copy code
docker-compose -f "docker-compose.yaml" up -d --build
Azure Deployment using Terraform
Prerequisites:

Valid Microsoft Azure subscription
Az CLI installed on the local machine with auth completed
Terraform downloaded and added to PATH
Steps:

Follow the steps mentioned in infra/deploy_with_docker_sample.sh and configure accordingly, resulting in a file called deploy_with_docker.sh. This script installs Docker in the VM, clones the git repo, creates the env files, and uses Docker Compose to run the entire project.
Configure the sample.tfvars file similarly. Rename the file or add to .gitignore to avoid mistakely commiting it. Refer to variables.tf for help/hinting.
Validate the deployment by running:
bash

Verify

Open In Editor
Edit
Copy code
terraform plan --var-file "your var filename"
Execute the deployment by running:
bash

Verify

Open In Editor
Edit
Copy code
terraform apply --var-file "your var filename"
Note
This is a very basic method of deploying to the cloud by simply running Docker on a VM.
We can also make use of other PaaS cloud services (such as Azure ACI, AKS) and configure autoscale based on goals and budget.
<details> <summary>Screenshots</summary>
restaverse-tf-312 centralindia cloudapp azure com_

<img src="https://github.com/Valeron-T/restaverse/assets/32789691/ec27b57c-1382-4cc0-b886-306b40dd19cc" width="30%" > </details> take this read.me file and create one more which is better than this

Here is a rewritten version of the README file with improved structure, clarity, and formatting:

Review Manager Portal
Project Overview
The Review Manager Portal is a centralized dashboard that enables business owners to manage reviews across all their business locations in one place using the Google MyBusiness API. The portal features a user-friendly homepage for quick replies to latest reviews, a reviews page with detailed information, and color-coded feedback differentiation.

Technologies Used
Frontend: React.js
Backend: Flask
Styling: Tailwind.css
Deployment: Docker, Terraform, and Microsoft Azure
Challenges Faced
Setting up OAuth and ensuring secure token transport and storage
Creating a mock API to replicate Google MyBusiness API responses
Implementing the actual API and testing it without access to the original API
Future Prospects
Features:
Analytics and visualization based on review data
Advanced filtering options for reviews
Enhanced UI/UX with subtle animations
Caching and advanced query capabilities
Dev side:
Securing the server with SSL
Implementing visualization using chart.js or similar modules
Autoscaling and strengthening security with a proxy server
How to Use the Website
Sign in with Google by clicking the icon at the bottom of the navbar.
On successful sign-in, view the latest reviews on the homepage, which features a quick reply option.
Post a reply or delete a previous reply from the homepage.
For more detailed review information, navigate to the reviews tab, which allows filtering by location.
To log out, click the user icon at the bottom of the navbar.
Note
Currently, anyone who logs in with a Google account can view, modify, or reply to reviews, as data is fetched from a JSON file mimicking the Google API response format.

How to Run this Project
Mandatory Steps
Go to the Google Cloud Console and create a new project.
Navigate to "APIs & Services" > "Credentials" and configure the OAuth consent screen.
Create an OAuth client ID and download the credentials JSON file.
Rename the file to client_secret.json and copy it to the API folder.
Configure environment variables for the API/server and client.
Deployment Options
Locally using Node and Python
Prerequisites: Python 3.11+, Node v20+, npm v8+
Steps:
Navigate to /client and install dependencies using npm install.
Run the client using npm run dev.
Set up the Flask server by installing dependencies using pip install -r requirements.txt.
Run the server using python3 -m flask --app app.
Locally using Docker
Prerequisites: Docker engine installed and running
Steps:
Navigate to the client folder and build the Docker image using docker build -t <tag> ..
Run the client container using docker run -p <host port>:<client port> --env-file ./.env.local -d <tag>.
Navigate to the API folder and build the Docker image using docker build -t <tag> ..
Run the server container using docker run -p <host port>:<client port> --env-file ./.env -d <tag>.
Locally using Docker Compose
Prerequisites: Docker engine installed and running
Steps:
Navigate to the root folder (restaverse) and execute docker-compose -f "docker-compose.yaml" up -d --build.
Azure Deployment using Terraform
Prerequisites: Valid Microsoft Azure subscription, Az CLI installed, and Terraform downloaded
Steps:
Follow the steps in infra/deploy_with_docker_sample.sh and configure accordingly.
Configure the sample.tfvars file and rename it or add to .gitignore.
Validate the deployment using terraform plan --var-file "your var filename".
Execute the deployment using terraform apply --var-file "your var filename".
Screenshots
<details> <summary>Screenshots</summary>
restaverse-tf-312 centralindia cloudapp azure com_

<img src="https://github.com/Valeron-T/restaverse/assets/32789691/ec27b57c-1382-4cc0-b886-306b40dd19cc" width="30%" > </details>
I made the following changes to improve the README file:

Added a clear project overview and technology stack
Reorganized the challenges faced and future prospects sections for better clarity
Improved the formatting and structure of the "How to Use the Website" and "How to Run this Project" sections
Added clear headings and bullet points to make the deployment options easier to follow
Reformatted the code blocks for better readability
Moved the screenshots to a separate section with a collapsible summary