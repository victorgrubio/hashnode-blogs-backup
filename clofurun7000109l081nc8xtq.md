---
title: "How to Dockerize a React App and Deploy It Easily"
seoTitle: "How to Dockerize a React App and Deploy It Easily"
seoDescription: "Discover how to quickly dockerize a React app and get it ready for deployment in just a few easy steps."
datePublished: Wed Nov 01 2023 14:28:22 GMT+0000 (Coordinated Universal Time)
cuid: clofurun7000109l081nc8xtq
slug: how-to-dockerize-a-react-app-and-deploy-it-easily
canonical: https://mentorcruise.com/blog/how-to-dockerize-a-react-app-and-deploy-it-easily/
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698848497931/970eb11b-1aab-416f-86c2-109b79ba825b.png
tags: docker, nginx, reactjs, typescript, docker-images

---

  
Do you want to learn how to dockerize a React app and make it ready for deployment? In this article, I’ll show you how to do that with a practical example from my [GitHub repo](https://github.com/victorgrubio/blog-projects/tree/main/react-nginx-dockerization).

**Originally published at MentorCruise:** [How to Dockerize a React App and Deploy It Easily - MentorCruise](https://mentorcruise.com/blog/how-to-dockerize-a-react-app-and-deploy-it-easily/)

### **Prerequisites**

Ensure you have a foundational understanding of React, Docker, and basic shell scripting. Ensure Docker and Node.js are installed on your machine, and you have a code editor ready for some hands-on action!

### **Understanding the React Application Structure**

The React application in our repository is structured with various components, dependencies, and configurations. The app is a simple goal tracker that lets you add, edit, and delete your goals. It uses React Hooks, React Router, and Axios to create a dynamic and interactive UI. The app also communicates with a backend API that uses MongoDB as the database. The app’s structure is as follows: 

* `package.json`: This file defines the dependencies and scripts for the app. We use libraries such as react, react-dom, react-router-dom, axios, and bootstrap.
    
* `src/index.js`: This file renders the main App component and wraps it with a BrowserRouter component to enable routing.
    
* `src/App.js`: This file defines the App component, which contains the main layout and logic of the app. It uses useState and useEffect hooks to manage the state and fetch data from the API. It also uses Switch and Route components to render different pages based on the URL path.
    
* `src/components`: This directory contains the reusable components for the app, such as GoalList, GoalForm, GoalItem, Navbar, and Footer. Each component has its file with a .jsx extension.
    
* `src/pages`: This directory contains the components for the different pages of the app, such as Home, About, and NotFound. Each page has its file with a .jsx extension.
    
* `src/styles`: This directory contains the custom CSS styles for the app. We use Bootstrap as a base framework and override some styles in our files.
    

### **Crafting a Multi-Stage Dockerfile**

The Dockerfile in the `frontend` directory employs a multi-stage build to create an optimized Docker image:

* **Stage 1: Building the React Application** 
    
* Utilizes `node:16.3.0-alpine` for a lightweight build environment. Installs dependencies and builds the application using `npm`.
    
* Utilizes `node:16.3.0-alpine` for a lightweight build environment.
    
* Installs dependencies and builds the application using `npm`.
    
* **Stage 2: Setting Up the Nginx Server** 
    
* Adopts `nginx:alpine` to serve the built React application. Copies the build artifacts and custom Nginx configuration for serving the application.
    
* Adopts `nginx:alpine` to serve the built React application.
    
* Copies the build artifacts and custom Nginx configuration for serving the application.
    

### **Parameterizing Nginx Configuration**

The custom Nginx configuration (`custom-nginx.template`) is designed to proxy API requests to a backend service and serve the React application for other routes. A shell script ([`generate-config.sh`](https://github.com/victorgrubio/blog-projects/tree/main/react-nginx-dockerization)) dynamically generates the final Nginx configuration by substituting environment variables, providing flexibility to define the backend host at runtime.

### **Orchestrating Containers with Docker Compose**

Docker Compose is a tool that lets you define and run multiple containers using a YAML file. It simplifies the process of building, running, and connecting containers.

The `docker-compose.yaml` file orchestrates the frontend and backend services, ensuring they can communicate and are deployed cohesively:

### **Local Development & Testing**

To run the Dockerized React app locally, use `docker-compose up` to build and start the containers. Ensure the application communicates with the backend API effectively and debug using Docker logs and browser developer tools.

### **CI/CD Considerations for Dockerized React Apps**

Integrating CI/CD pipelines, like GitHub Actions, can automate the build, test, and deployment of the Dockerized React app. Define workflows in `.github/workflows` to trigger code pushes or pull requests, ensuring continuous delivery and integration.

#### **Build Worfklow**

This workflow triggers every push or pull request to the main branch. It builds and tests both frontend and backend images using Docker commands. It also pushes the images to a Docker registry (such as Docker Hub or GitHub Packages) using secrets to store credentials. We have commented it out on our repo to avoid additional build runs. The code we've used is the following:

### **Best Practices & Tips**

* Optimize Dockerfile: Leverage Docker layer caching by ordering instructions to install dependencies before copying all source files.
    
* Manage Images: Regularly prune unused Docker images and containers to manage disk usage.
    
* Security: Ensure only necessary ports are exposed and use trusted base images.
    

### **Conclusion**

I hope you enjoyed this guide on how to dockerize a React app and make it deployable. You learned how to use Docker, Nginx, and Docker Compose to set up a uniform environment for your app in different phases of development, testing, and production. This will help you streamline your DevOps process and create better software.

If you liked this article, you can check my other blog posts and my mentorships plans at my [MentorCruise Profile](https://mentorcruise.com/mentor/victorgarcia/).

Thanks for reading!

### **References**

Source code: [GitHub repository](https://github.com/victorgrubio/blog-projects/tree/main/react-nginx-dockerization)