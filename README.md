# 🐍 Python Application with Jenkins CI/CD Pipeline 🚀

![image](https://github.com/user-attachments/assets/f35d40a5-e9da-4b44-bc00-934f7b1770f1)


## 📌 Project Overview
This project demonstrates a simple Python application with a complete **CI/CD pipeline** using **Jenkins, Docker, and GitHub**. The application provides a **command-line tool** that adds two numbers together, with automated testing and continuous integration/deployment.

> ⚠️ **Note:** Ensure **Docker Desktop** is running in the background before executing any Docker-related commands.

---

## 🏗️ Project Components

### 📂 **Project Structure**
```
.
├── sources/
│   ├── add2vals.py      # 🎯 Main application entry point
│   ├── calc.py          # 🧮 Core calculation module
│   └── test_calc.py     # 🧪 Unit tests
├── dist/               # 📦 Compiled executables
├── requirements.txt    # 📜 Python dependencies
├── Jenkinsfile        # ⚙️ Pipeline configuration
├── docker-compose.yml # 🐳 Docker setup
└── README.md         # 📖 Project documentation
```

### 🐍 **Python Application**
- **`add2vals.py`**: 🎯 Handles command-line arguments and displays results.
- **`calc.py`**: 🧮 Core calculation module containing the addition logic.
- **`test_calc.py`**: 🧪 Unit tests for the calculation module.
- **`requirements.txt`**: 📜 Lists Python dependencies with specific versions.

### 🏗️ **Jenkins Pipeline**
- **`Jenkinsfile`**: ⚙️ Defines the CI/CD pipeline workflow.
- **`docker-compose.yml`**: 🐳 Configures Jenkins and its agents with volume mappings and network settings.

### 🐳 **Docker Configuration**
- **Jenkins container**: 🏗️ Main Jenkins server with persistent storage.
- **Jenkins agent container**: ⚡ For distributed builds.
- **Python build container**: 🏭 Used for building and testing the application.

---

## 🔧 Steps to Perform This Project

### **Step 1: 🛠️ Setup Jenkins**

#### 1️⃣ Pull Jenkins Image and Start Containers
```sh
docker-compose up -d
```
![WhatsApp Image 2025-04-02 at 16 41 52_be69c68f](https://github.com/user-attachments/assets/4613b822-505a-4aaf-9660-73dd0d99f02d)


#### 2️⃣ Get Initial Admin Password
```sh
docker-compose exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```
![WhatsApp Image 2025-04-02 at 16 42 00_c8ea0217](https://github.com/user-attachments/assets/93dec92a-4e19-41aa-b022-791e537661c2)

#### 3️⃣ Access Jenkins 🌍
- Open a browser and go to: **http://localhost:8080**
- Enter the **initial admin password** from step 2️⃣

  ![WhatsApp Image 2025-04-02 at 16 48 56_cdb782a6](https://github.com/user-attachments/assets/98b06ec8-028c-4345-9f54-f77a3cfbd1d6)


#### 4️⃣ Install Plugins 🔌
- Click **Install suggested plugins** and wait for installation to complete.

  ![image](https://github.com/user-attachments/assets/95357f39-5e40-4016-9545-bbc48faa83b9)

  ![WhatsApp Image 2025-04-02 at 16 49 11_6421c1e3](https://github.com/user-attachments/assets/c46e6023-aba8-400b-8b6e-c1f0645e7a73)



#### 5️⃣ Create First Admin User 👤
- Enter your desired **username, password, and email**.
- Click **Save and Continue**.

  ![WhatsApp Image 2025-04-02 at 16 49 43_a38d36b5](https://github.com/user-attachments/assets/6dad7174-bd71-4457-bb7a-d6e4605942fc)


#### 6️⃣ Configure Jenkins Instance ⚙️
- Keep the default URL: **http://localhost:8080/**
- Click **Save and Finish**.

  ![image](https://github.com/user-attachments/assets/03024119-819a-46db-ab30-3f4dc44dffae)

  ![image](https://github.com/user-attachments/assets/2a0527c0-b767-43a9-91d8-3450029ba918)



#### 7️⃣ Create a Pipeline Project 🚀
1. Click **New Item**
2. Enter project name: `simple-python-pyinstaller-app`
3. Select **Pipeline** and click **OK**
4. In the pipeline configuration:
   - Scroll to the **Pipeline** section
   - Select **Pipeline script from SCM**
   - Choose **Git** as SCM
   - Enter repository URL: `https://github.com/TarakKatoch/Jenkins-Orchestration.git`
   - Enter **branch specifier**: `*/master`
   - Click **Save**
  
     ![WhatsApp Image 2025-04-02 at 16 50 00_fe2edbf8](https://github.com/user-attachments/assets/f014e02b-501d-4a3b-a47a-f606189b5e0f)

     ![WhatsApp Image 2025-04-02 at 16 50 17_fb4424be](https://github.com/user-attachments/assets/4c870050-7764-4e1e-9f53-9896c424d707)



#### 8️⃣ Install and Configure Docker in Jenkins Container 🐳
```sh
# Install Docker inside Jenkins container
docker-compose exec jenkins bash -c "apt-get update && apt-get install -y docker.io"

# Start Docker service
docker-compose exec jenkins bash -c "service docker start"

# Verify Docker installation
docker-compose exec jenkins docker --version
```
![WhatsApp Image 2025-04-02 at 16 43 07_5d0e7b36](https://github.com/user-attachments/assets/57639c1e-bc10-4260-bbf8-6c2d208e3fe6)

![WhatsApp Image 2025-04-02 at 16 43 14_08c94a3f](https://github.com/user-attachments/assets/c17c1768-a807-4447-b52f-744545bbd629)

![WhatsApp Image 2025-04-02 at 16 43 20_04271ac3](https://github.com/user-attachments/assets/be84ad01-5c76-44f5-a33c-aa7c34bcc4e8)




#### 9️⃣ Install Docker Plugins 🔌
- Navigate to **Manage Jenkins > Manage Plugins**
- Under **Available** tab, search for and install:
  - **Docker Pipeline**
  - **Docker plugin**
  - **docker-build-step**

![WhatsApp Image 2025-04-02 at 16 50 32_a1fa4d36](https://github.com/user-attachments/assets/dd33d1a4-fd78-4942-99ad-f05a1f95601f)

![WhatsApp Image 2025-04-02 at 16 50 43_fedf5192](https://github.com/user-attachments/assets/264f335f-5760-4611-a44b-64d89644ac9c)


#### 🔟 Restart Jenkins After Plugin Installation 🔄
```sh
docker-compose restart jenkins
```
- Wait for Jenkins to restart (~30 seconds)
- Verify Jenkins is running:
```sh
docker-compose ps
```
![WhatsApp Image 2025-04-02 at 16 43 42_ee633331](https://github.com/user-attachments/assets/c8a53f64-dbe6-494e-a9a0-3e4ed8ecfeab)

![WhatsApp Image 2025-04-02 at 16 43 49_24868647](https://github.com/user-attachments/assets/7b92cad1-2f83-4daa-a32d-bad2ced9b287)



#### 🔑 Sign in to Jenkins 🔐
- Use the credentials created in **step 5️⃣**

  ![WhatsApp Image 2025-04-02 at 16 51 02_53992c8a](https://github.com/user-attachments/assets/753de638-dc3c-41dc-bb48-2158b33536ab)


#### ▶️ Run the Pipeline 🚦
- Go to **Jenkins Dashboard** → Open **simple-python-pyinstaller-app**
- Click **Build Now**

---

![WhatsApp Image 2025-04-02 at 21 07 06_088201c3](https://github.com/user-attachments/assets/f27737ac-1168-4147-abf3-20c0925be67e)

![WhatsApp Image 2025-04-02 at 21 06 50_448eb920](https://github.com/user-attachments/assets/c18a5d12-6601-4bb4-9ff2-8e2acae869c8)



### **Step 2: 🛠️ Testing the Executable**

#### 📥 Download the Executable from Jenkins 💾
1. Open **Jenkins Dashboard**
2. Click on **simple-python-pyinstaller-app**
3. Click on the **latest build number**
4. Under **Build Artifacts**, download `add2vals`

![WhatsApp Image 2025-04-02 at 21 06 51_a8777096](https://github.com/user-attachments/assets/8b966789-b5cf-4158-8ad9-a0c533eee847)


> ⚠️ **Note:** The executable is a Linux version since Jenkins runs in a Linux container.

#### ▶️ Run the Executable on Windows Using WSL 💻
```sh
# Check if WSL is installed
wsl --version

# If not installed, run:
wsl --install

# Restart computer and verify installation:
wsl --version

# Open WSL terminal
wsl

# Navigate to the download directory in WSL
cd /mnt/c/Users/asus/OneDrive/Downloads

# Make the file executable
chmod +x add2vals

# Run the executable
./add2vals 5 3
```

---

## 📌 **What Does PyInstaller Do?**
PyInstaller creates a **standalone executable** from the Python application.

### 🔍 **Phases of PyInstaller**
1️⃣ **Analysis Phase**: Scans dependencies, identifies required files, and builds a dependency graph.
2️⃣ **Bundling Phase**: Packages dependencies, Python interpreter, and resources into a single executable.
3️⃣ **Output**: Generates an executable stored in the `dist/` directory.

### 🌟 **Benefits of PyInstaller**
✅ **Portability**: No Python installation required, easy distribution.
✅ **Dependency Management**: Includes all required libraries.
✅ **Cross-Platform Support**: Generates executables for Windows, Linux, and macOS.

---

## 🎯 **Conclusion**
This project successfully sets up a **CI/CD pipeline** with **Jenkins, Docker, and PyInstaller**. By following the steps above, you have:

✔️ Set up a **Jenkins server** with Docker support.
✔️ Created a **pipeline** that automatically **builds, tests, and packages** the application.
✔️ Generated a **standalone executable** that runs on any system.

### 🎉 **Thank You!**
If you found this guide helpful, consider:
- ⭐ **Starring this repository**.
- 📢 **Sharing it with others**.
- 🛠️ **Contributing improvements**.
- 📝 **Reporting any issues you encounter**.

Happy coding! 🚀

