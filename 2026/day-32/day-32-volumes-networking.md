# Day 32: Docker Volumes & Networking

## Task 1: Understanding Data Persistence in Containers

1. **Start a database container (Postgres/MySQL):**
    ```sh
    docker run -d --name dbtest postgres
    ```
2. **Connect to the database and create a table with some data.**
3. **Stop and remove the container:**
    ```sh
    docker stop dbtest
    docker rm dbtest
    ```
4. **Start a new container (without volumes):**
    ```sh
    docker run -d --name dbtest2 postgres
    ```
5. **Check if your data is still there.**

**Result:**  
The data is **lost** after removing the original container.

**Explanation:**  
By default, container data is stored in the container’s writable layer, which is deleted when the container is removed. To persist data, you need to use volumes or bind mounts.

## Task 1: The Problem

- **Run a Postgres/MySQL container.**
- **Create data (table, rows).**
- **Stop & remove the container.**
- **Run a new one — is your data still there?**

**What happened:**  
The data is **lost** after removing the container.  
**Why:**  
By default, container data is stored in the container's writable layer, which is deleted when the container is removed.

---

## Task 2: Named Volumes

- **Create a named volume:**  
    `docker volume create mydbdata`
- **Run DB container with volume:**  
    `docker run -d --name db -v mydbdata:/var/lib/postgresql/data postgres`
- **Add data, stop & remove container.**
- **Run new container with same volume:**  
    `docker run -d --name db2 -v mydbdata:/var/lib/postgresql/data postgres`
- **Is data still there?**  
    **Yes,** data persists because it's stored in the named volume.

**Verify:**  
- `docker volume ls`  
- `docker volume inspect mydbdata`

---

## Task 3: Bind Mounts

- **Create a folder with `index.html` on host.**
- **Run Nginx with bind mount:**  
    `docker run -d -p 8080:80 -v /path/to/folder:/usr/share/nginx/html nginx`
- **Access page in browser.**
- **Edit `index.html` on host, refresh browser.**

**Difference:**  
- **Named volume:** Managed by Docker, data stored in Docker's storage location.  
- **Bind mount:** Direct mapping to a host directory, changes on host are reflected in the container instantly.

---

## Task 4: Docker Networking Basics

- **List networks:**  
    `docker network ls`
- **Inspect default bridge:**  
    `docker network inspect bridge`
- **Run two containers on bridge:**  
    `docker run -it --rm --name c1 busybox`  
    `docker run -it --rm --name c2 busybox`
- **Ping by name:**  
    Usually **does not work** on default bridge.
- **Ping by IP:**  
    **Works** if you use the container's IP address.

---

## Task 5: Custom Networks

- **Create custom network:**  
    `docker network create my-app-net`
- **Run two containers on it:**  
    `docker run -it --rm --name a1 --network my-app-net busybox`  
    `docker run -it --rm --name a2 --network my-app-net busybox`
- **Ping by name:**  
    **Works** on custom bridge networks.

**Why?**  
Custom bridge networks enable Docker's embedded DNS, allowing containers to resolve each other's names. The default bridge does not.

---

## Task 6: Put It Together

- **Create custom network:**  
    `docker network create dev-net`
- **Run DB with volume:**  
    `docker run -d --name db --network dev-net -v mydbdata:/var/lib/postgresql/data postgres`
- **Run app on same network:**  
    `docker run -it --rm --network dev-net appropriate/curl ping db`
- **Verify:**  
    The app container can reach the database by container name (`db`).
