Below is the content and explanation of my Dockerfile-

**FROM node:18-alpine**
(This line says: "Start with a small and fast version of Node.js (version 18 with Alpine Linux).")

**WORKDIR /usr/src/app**
(This sets the working directory inside the container where all your code and files will go)

****COPY package*.json ./****
**RUN npm install**
(This copies the package.json file (which lists your app's dependencies) and installs those dependencies)

**COPY . .**
(This copies all the remaining files (like app.js) into the container)

**EXPOSE 8080**
(This tells Docker that your app will run on port 8080, so it can be accessed there)

**CMD ["node", "app.js"]**
(This runs your Node.js app when the container starts)

**Core Concept Questions**
**Question-1: Why is Docker useful in building and deploying microservices?**
Docker is useful because it keeps everything our app needs (like code, libraries, settings) in one neat package called a container. That container works the same everywhere – on our laptop, a friend’s computer, or a cloud server.
For example, in a banking app, we might have different parts like:
Login service
Payments service
Notifications service
Each of these can be made as a small app (microservice), and Docker helps run and manage them individually without breaking each other.

**Question-2: What is the difference between a Docker image and a container?**
- Image: A read-only template that contains the application and environment.
- Container: A running instance of the image.
In scaling, multiple containers can be launched from the same image to handle load across distributed systems.
A Docker image is like a recipe. It has all the steps and ingredients to create a dish (our app). A Docker container is the actual dish made from that recipe – it’s the running version. If we want to run 10 copies of our web app (to handle lots of users), we use the same image to create 10 containers. That’s how it helps in scaling.

**Question-3: How does Kubernetes help when using Docker for big apps?**
Docker is great for running one or two apps. But what if our app becomes huge and needs to run hundreds of containers? This is where Kubernetes helps us:
It automatically starts, stops, or restarts containers if needed.
It spreads containers across multiple servers.
It handles load balancing, so no server gets overloaded.
It can update your app without downtime.
For example- Imagining running an online shopping app during a Diwali sale – traffic is huge. Kubernetes makes sure the app stays fast and stable even with thousands of users.
