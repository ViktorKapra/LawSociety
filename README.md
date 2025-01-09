# LawSociety

This project is a template for a web application that uses React for the frontend and .NET for the backend.

### Technologies Used:
- **React**: A JavaScript library for building user interfaces.
- **Vite**: A build tool that provides a faster and leaner development experience for modern web projects.
- **.NET**: A free, cross-platform, open-source developer platform for building many different types of applications.
- **Docker**: Used to containerize the application for consistent and reproducible environments.
- **JavaScript**: For dynamic client-side scripting.
- **C#**: For building the backend server-side logic.
- **CSS**: For styling the web application.
- **HTML**: The standard markup language for creating web pages.

### Features:
- **Fast Development Environment**: Utilizes Vite for a quick start and efficient development process with HMR.
- **Modular Codebase**: Clean separation of frontend and backend concerns.
- **Containerization**: Docker support for easy deployment and environment management.

### Getting Started:
1. **Clone the repository**:
    ```bash
    git clone https://github.com/ViktorKapra/LawSociety.git
    ```
2. **Navigate to the project directory**:
    ```bash
    cd LawSociety
    ```
3. **Install dependencies**:
    ```bash
    cd lawsociety.client
    npm install
    ```
4. **Run the application**:
    ```bash
    cd LawSociety.Server
    dotnet run
    ```
!! If you are using Visual studio just open LawSociety.sln !!
### CI/CD Process
#### Continuous Integration (CI)

The CI process for this repository is defined in the `main.yml` file and is triggered on:
- Push 
- Pull requests targeting the `main` or `development` branches

The CI workflow is runned on `ubuntu-latest` and consists of four jobs:

1. **Build Job**
   - Builds the the project

2. **Unit Test Job**
   - Runs Xunit test on the backend 

3. **Style Lint Job**
   - Runs Linter and .NET format 

4. **Security Check Job**
   - Runs on **Snyc** and check for vulnerabilities

#### Continuous Deployment (CD)

The CD process is defined in the `CD.yml` file and is triggered on:
- Push to the `development`, `main` branches
- Pull requests targeting the `development` and `main` branches

The CD workflow consists of a single job:

1. **Build and Push Job**
   - Ont this job is build an docker image of the project. Then the image is checked with **Trivy** and finaly it is push to DockerHub.
