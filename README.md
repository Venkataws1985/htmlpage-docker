
---

## **Step 1: Upload Your Files to GitHub**
### **1. Create a GitHub Repository**
- Go to [GitHub](https://github.com/)
- Click **New repository**
- Give it a name, e.g., `docker-html-host`
- Keep it **public** and **initialize with a README**
- Click **Create repository**

### **2. Clone the Repository Locally**
If you have Git installed, open **VSCode Terminal** and run:

```sh
git clone https://github.com/your-username/docker-html-host.git
cd docker-html-host
```

Replace `your-username` with your actual GitHub username.

### **3. Add Your HTML File and Dockerfile**
Inside your cloned repository, create `index.html`:

```sh
<!DOCTYPE html>
<html>
<head>
    <title>My Dockerized HTML Page</title>
</head>
<body>
    <h1>Hello, World! Hosted from GitHub and running in Docker Playground.</h1>
</body>
</html>
```

Create a `Dockerfile`:

```sh
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/
EXPOSE 80
```

### **4. Push to GitHub**
Now, push these files to GitHub:

```sh
git add .
git commit -m "Added HTML and Dockerfile"
git push origin main
```

---

## **Step 2: Run in Docker Playground**
Now that your files are on GitHub, follow these steps in Docker Playground:

### **1. Open Docker Playground**
Go to [Docker Playground](https://labs.play-with-docker.com/) and start a new session.

### **2. Clone Your GitHub Repository**
In Docker Playground, run:

```sh
git clone https://github.com/your-username/docker-html-host.git
cd docker-html-host
```

### **3. Build the Docker Image**
Run:

```sh
docker build -t my-html-server .
```

### **4. Run the Container**
Run:

```sh
docker run -d -p 8080:80 my-html-server
```

### **5. Get the URL to Access**
Run:

```sh
docker ps
```

- Note the **Container ID**.
- Click **Open Port** in Docker Playground and enter `8080`.
- Your HTML page should now be accessible.

---

## **Step 3: Automate with Docker Hub (Optional)**
If you want to **skip cloning the repository manually**, you can push your image to **Docker Hub** and pull it directly from Docker Playground.

### **1. Log in to Docker Hub**
Create an account at [Docker Hub](https://hub.docker.com/) and then login:

```sh
docker login
```

### **2. Tag and Push the Image**
Replace `your-dockerhub-username`:

```sh
docker tag my-html-server your-dockerhub-username/my-html-server
docker push your-dockerhub-username/my-html-server
```

### **3. Run in Docker Playground Without Cloning**
Now, in Docker Playground, simply run:

```sh
docker run -d -p 8080:80 your-dockerhub-username/my-html-server
```

---