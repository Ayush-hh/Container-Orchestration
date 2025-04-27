![WhatsApp Image 2025-04-27 at 20 26 34_302b16cb](https://github.com/user-attachments/assets/7f5a7097-21de-4dc5-9094-138983da13a5)![WhatsApp Image 2025-04-27 at 20 26 07_02889c58](https://github.com/user-attachments/assets/63ca8b19-6af9-4c7c-ba7a-169861b6f344)# 🐳 Dockerized Streamlit Development Environment

## 🚀 Prerequisites
Before setting up the environment, ensure you have the following installed on your machine:

- *Docker* 🐳 (Ensure the Docker daemon is running)
- *Python 3.9+* 🐍 (Verify installation with python --version)
- *pip* (Ensure it's installed and up to date with pip --version)
- *Basic knowledge of Streamlit* 📊

---

## 📂 Directory Structure

project_root/
│── .streamlit/
│   └── config.toml
│── src/
│   └── main.py
│── Dockerfile
│── requirements.txt
│── README.md


---

## 📜 File Explanations

### 1️⃣ .streamlit/config.toml
This file configures Streamlit settings for local development.
toml
[server]
headless = true
runOnSave = true
fileWatcherType = "poll"


### 2️⃣ src/main.py
This file contains the core logic of the Streamlit application. It includes:
- *A home page* 🏠 that provides an introduction to the app.
- *A data explorer* 📊 allowing users to upload and inspect CSV files.
- *A visualization page* 📈 that generates interactive charts and graphs.

### 3️⃣ Dockerfile
Defines the containerized environment.
dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt
COPY . /app/
EXPOSE 8501
CMD ["streamlit", "run", "src/main.py", "--server.port=8501", "--server.address=0.0.0.0"]


### 4️⃣ requirements.txt
Contains necessary dependencies:

streamlit
pandas
numpy
matplotlib
plotly


## ⚡ Steps to Run the Project

1️⃣ Build the Docker image:
sh
docker build -t streamlit-app .

![Image](https://github.com/user-attachments/assets/a6e52a0d-8bec-4497-b915-aa9fbdb1510d)

2️⃣ Run the container:
sh
docker run -p 8501:8501 streamlit-app

![Image](https://github.com/user-attachments/assets/3dddbb43-133b-480c-b104-4ff58e9b2371)

3️⃣ Open in Browser: Go to [http://localhost:8501](http://localhost:8501) 🌐

![Image](https://github.com/user-attachments/assets/181ca676-06af-4197-b28e-36a8c69061b3) 
---

## 🎯 Conclusion
You now have a fully functional Streamlit environment running inside Docker! 🚀
