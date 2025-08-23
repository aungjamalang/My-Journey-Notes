# 🌟 Mobile Security Framework (MobSF) Docker Setup 🚀

Welcome to the vibrant guide for setting up the **Mobile Security Framework (MobSF)** using Docker! 🎉 Follow these steps to get MobSF up and running, and dive into mobile app security analysis with ease! 🔒

## 🛠️ Prerequisites
Before you begin, ensure you have:
- **Docker** 🐳: Installed and running. Grab it from [Docker's official website](https://www.docker.com/get-started) if you haven’t already! 📥
- **Network Access** 🌐: Make sure port `8000` is free on your host machine, or tweak the port mapping if needed. 🔌

## 🚀 Steps to Set Up MobSF with Docker

### 1. 🎯 Pull the MobSF Docker Image
Let’s fetch the latest MobSF image from Docker Hub with this shiny command:

```bash
docker pull opensecurity/mobile-security-framework-mobsf:latest
```

This grabs the freshest version of MobSF from OpenSecurity. 🌈

### 2. 🏃 Run the MobSF Container
Time to launch MobSF and get that web interface sparkling! ✨ Run this command:

```bash
docker run -it --rm -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest
```

**What’s Happening Here?** 🤔
- `-it`: Puts you in interactive mode with a terminal. 🖥️
- `--rm`: Poof! 🪄 The container vanishes when you stop it, keeping things tidy.
- `-p 8000:8000`: Links port `8000` on your machine to `8000` in the container, opening the door to MobSF’s web interface. 🚪
- `opensecurity/mobile-security-framework-mobsf:latest`: The star of the show—the MobSF image! 🌟

### 3. 🌐 Access the MobSF Web Interface
Once the container is up and running:
1. Fire up your favorite web browser. 🦊🌍
2. Head to `http://localhost:8000`. 🔗
3. Log in with these default credentials:
   - **Username**: `mobsf` 🧑‍💻
   - **Password**: `mobsf` 🔑

**⚠️ Pro Tip**: Change the default password after logging in to keep things secure! 🔐 Check the [MobSF documentation](https://mobsf.github.io/docs/) for details on user management. 📖

## 🎨 Additional Notes
- **Container Cleanup** 🧹: The `--rm` flag ensures the container disappears when you’re done. Want to keep data like analysis reports? Mount a volume like `-v mobsf_data:/root/.MobSF`. 📂
- **Port Conflicts** 🚨: If `8000` is taken, switch it up (e.g., `-p 8080:8000`) and visit `http://localhost:8080`. 🔄
- **Explore More** 📚: For advanced setups, troubleshooting, or cool features, dive into the [official MobSF documentation](https://mobsf.github.io/docs/). 🌍

## 🛑 Stopping the Container
To stop MobSF and clean up:
1. Hit `Ctrl+C` in the terminal where the container is running. 🛑
2. Thanks to `--rm`, the container will vanish like magic! 🎩

Happy analyzing, and stay secure! 🛡️💻
