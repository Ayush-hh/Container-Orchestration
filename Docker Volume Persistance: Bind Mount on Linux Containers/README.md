# 🚀 Docker Volume Persistence: Bind Mounts on Linux Container 🐳

## 📌 Introduction
This experiment demonstrates how to use Docker *bind mounts* with a *Linux container* to persist data beyond a container’s lifecycle. By mounting a local directory into a container, data remains accessible even after the container is removed.

---

## 🔧 Steps & Observations

### 🏗 Step 1: Running a Container with a Bind Mount
You executed:
sh
docker run -dit --name alpine_with_bind_mount -v D:\Anugrah\UPES\Semester6\Container Orchestration & automation\Docker Exp\Docker Volume Persistence, Bind Mounts with Linux Containers:/data alpine:latest sh

![Image](https://github.com/user-attachments/assets/2a9ed21d-eafc-4219-a55c-96e5b731199e)
#### 🔍 What Happened?
- Since alpine:latest was not found locally, Docker pulled it from the official repository.
- A new container named *alpine_with_bind_mount* was created.
- The -v flag mounted the local directory D:\Anugrah\UPES\Semester6\Container Orchestration & automation\Docker Exp\Docker Volume Persistence, Bind Mounts with Linux Containers to /data inside the container.
- The container started a shell (sh) in detached mode.

---

### 📄 Step 2: Creating a File Inside the Bind Mount
Inside the container, you created a file:
sh
docker exec -it alpine_with_bind_mount sh -c "echo 'Hello, Anugrah!' > /data/testfile.txt"

![Image](https://github.com/user-attachments/assets/aef4183e-d45f-4d9d-86d3-3ac3dbb8e0ed)
#### 🔍 What Happened?
- The command executed a shell inside the running container.
- It created a file testfile.txt inside /data and wrote *"Hello, Anugrah!"* into it.
- Since /data is a bind-mounted directory, the file was actually stored in D:\Anugrah\UPES\Semester6\Container Orchestration & automation\Docker Exp\Docker Volume Persistence, Bind Mounts with Linux Containers on the host.

---

### ✅ Step 3: Verifying the File Exists
To check the contents:
sh
docker exec -it alpine_with_bind_mount sh -c "cat /data/testfile.txt"

![Image](https://github.com/user-attachments/assets/74de0f5c-d9ba-454e-9c7a-229acac17fb7)
#### 📌 Output:

Hello, Ayush!

![Image](https://github.com/user-attachments/assets/74de0f5c-d9ba-454e-9c7a-229acac17fb7)
This confirms that the file was successfully created and accessible inside the container. 🎉

---

### 🗑 Step 4: Removing the First Container
You removed the container:
sh
docker rm -f alpine_with_bind_mount

![Image](https://github.com/user-attachments/assets/b4d5bdf6-b8b1-4d68-95fb-f01654694b04)
#### 🔍 What Happened?
- The container was *forcefully stopped and removed*.
- However, since testfile.txt was inside the bind-mounted directory, it *remained on the host system*. 🏠

---

### 🔄 Step 5: Creating a New Container with the Same Bind Mount
You started a new container:
sh
docker run -dit --name new_alpine -v D:\Anugrah\UPES\Semester6\Container Orchestration & automation\Docker Exp\Docker Volume Persistence, Bind Mounts with Linux Containers:/data alpine sh

![Image](https://github.com/user-attachments/assets/2ee6ef7f-f405-4b55-b397-a54efe97bbe0)
#### 🔍 What Happened?
- A new container named *new_alpine* was created.
- The same bind-mounted directory (D:\Anugrah\UPES\Semester6\Container Orchestration & automation\Docker Exp\Docker Volume Persistence, Bind Mounts with Linux Containers) was mounted to /data.

---

### 🔎 Step 6: Verifying File Persistence
Inside the new container, you checked if testfile.txt still exists:
sh
docker exec -it new_alpine sh -c "cat /data/testfile.txt"

![Image](https://github.com/user-attachments/assets/2ee6ef7f-f405-4b55-b397-a54efe97bbe0)
#### 📌 Output:

Hello, Ayush!

![Image](https://github.com/user-attachments/assets/2ee6ef7f-f405-4b55-b397-a54efe97bbe0)
This confirms that *bind mounts persist data even after a container is removed*. 🔥

---

## 🎯 Conclusion
✅ Bind mounts allow *data persistence across multiple container instances*.
✅ Deleting a container does *not* remove data stored in the bind-mounted directory.
✅ Any new container with the same mount can access previous container data.
✅ Useful for *sharing files between containers* and *persisting data beyond the container’s lifecycle*.

---

### 🚀 Next Steps
- 🛠 Experiment with *named volumes* (docker volume create) to manage persistent storage more efficiently.
- 🐳 Try using bind mounts with *different container images*.
- 🔐 Explore how *permissions* impact bind-mounted files across host and container.

---

🎯 This experiment showcases the power of bind mounts in Docker. Keep exploring, and happy coding! 🚀
