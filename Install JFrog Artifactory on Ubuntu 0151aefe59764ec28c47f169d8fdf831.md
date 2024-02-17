# Install JFrog Artifactory on Ubuntu

# **Step 1: Install Docker Engine**

After installing Docker, you need to add the current user to the **Docker** group so that even as a non-root user, you can run Docker operations. Include your current user in the docker group using these commands:

```bash
$ sudo usermod -aG docker $USER
$ newgrp docker
```

Restart your device to make the changes take effect.

# **Step 2: Download the JFrog Artifactory Docker image**

Now that you have Docker installed, you need to get the Artifactory Docker image. Think of Docker images as files that contain a set of instructions to execute code in a Docker Container.

### 1. Get the Docker images with these commands:

```bash
$ docker pull docker.bintray.io/jfrog/artifactory-oss:latest

# For CE edition

$ docker pull docker.bintray.io/jfrog/artifactory-cpp-ce
```

### 2. To confirm if the pulls were successful, check your current image list with this command:

```bash
$ docker images
```

![pasted image 0.png](Install%20JFrog%20Artifactory%20on%20Ubuntu%200151aefe59764ec28c47f169d8fdf831/pasted_image_0.png)

# **Step 3: Create a Data Directory**

To keep everything organized and persistent, we will create some directories in the host system. Create the directories and change their ownership with these commands:

```bash
$ sudo mkdir -p /jfrog/artifactory
$ sudo chown -R 1030 /jfrog/
```

# **Step 4: Start the JFrog Artifactory Container**

Now you have the necessary Docker images of JFrog Artifactory. It’s time to start the created container.

### 1. Run the Artifactory Container with this command:

```bash
docker -d --name artifactory -p 8082:8082 -p 8081:8081 -v artifactory-data:/var/opt/jfrog/artifactory release-docker.jfrog.io/jfrog/artifactory-pro:latest
```

### 2. After running the container, you can check its status using the following command:

```bash
$ docker ps
```

![pasted image 0 (1).png](Install%20JFrog%20Artifactory%20on%20Ubuntu%200151aefe59764ec28c47f169d8fdf831/pasted_image_0_(1).png)

# **Step 5: Access Artifactory Web Interface**

We’ve successfully run the Artifactory container. Now you can access it using any web browser. We will use ports 8081 and 8082 on the localhost to run the container.

### 1. To access the Artifactory web interface, open your web browser and paste any of these into the search bar:

**https://localhost:8081**

OR

**http://localhost:8082**

- Provide default admin username as “admin” and password as “password” then click on the **Login** button. You will see the Getting Started page.

# **Setting up Artifactory 4 as a PyPI repository in minutes**

[http://www.youtube.com/watch?v=tNSzJQ9gWrc&t=172s](http://www.youtube.com/watch?v=tNSzJQ9gWrc&t=172s)