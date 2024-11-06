# Dockerfile Explanation

This document explains each line of the Dockerfile configuration used to build and run a Node.js application in a Docker container.

---

## Dockerfile Contents

```dockerfile
# 1. Define the Base Image
FROM node:20-alpine3.20

# 2. Label for Maintainer Information
LABEL mantainer="Karis Omotosho"

# 3. Set the Working Directory
WORKDIR /usr/src/app

# 4. Copy the Application Code into the Container
COPY app .

# 5. Install Dependencies
RUN npm install

# 6. Expose the Application Port
EXPOSE 3000

# 7. Define the Default Command to Run the Application
CMD npm start app.js
```

---

### Explanation of Each Line

1. **Define the Base Image**

   ```dockerfile
   FROM node:20-alpine3.20
   ```

   This line specifies the base image that the container will use. Here, it uses the official Node.js image version `20` with the `alpine3.20` tag. The Alpine version is chosen as it's a lightweight Linux distribution, making the final container size smaller and more efficient.

2. **Label for Maintainer Information**

   ```dockerfile
   LABEL mantainer="Karis Omotosho"
   ```

   The `LABEL` instruction adds metadata to the image, such as the maintainer's name or contact information. Here, it identifies "Karis Omotosho" as the maintainer of this image.

3. **Set the Working Directory**

   ```dockerfile
   WORKDIR /usr/src/app
   ```

   The `WORKDIR` command sets the default working directory inside the container. It helps organize files by ensuring that all subsequent commands (such as copying files and running commands) operate within `/usr/src/app`.

4. **Copy the Application Code into the Container**

   ```dockerfile
   COPY app .
   ```

   The `COPY` command copies the contents of the `app` folder from your local directory (where the Dockerfile is located) to the working directory in the container (`/usr/src/app`). This places all necessary files for the app to run within the container.

5. **Install Dependencies**

   ```dockerfile
   RUN npm install
   ```

   The `RUN` command executes commands during the image build process. Here, it installs all necessary dependencies listed in the app's `package.json` using `npm install`.

6. **Expose the Application Port**

   ```dockerfile
   EXPOSE 3000
   ```

   The `EXPOSE` command informs Docker that the container will listen on port `3000` at runtime. This port should match the port the application listens on, allowing it to communicate with other containers or the host machine.

7. **Define the Default Command to Run the Application**

   ```dockerfile
   CMD npm start app.js
   ```

   The `CMD` instruction defines the default command that will run when the container starts. Here, `npm start app.js` will start the application by executing `app.js`. This command is executed in the container environment.

---

### Summary

This Dockerfile is designed to build a lightweight, efficient Node.js application image. It:

- Uses a slim, Alpine-based Node.js image.
- Copies application files and installs dependencies.
- Exposes the necessary port and defines a command to start the application.

This configuration provides an efficient way to package, distribute, and run a Node.js application in a Docker container.
