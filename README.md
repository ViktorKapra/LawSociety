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
- Push to the main, development, hotfi
- Pull requests targeting the `main` or `development` branches

The CI workflow consists of four jobs:

1. **Build Job**
   - Runs on `ubuntu-latest`
   - Steps:
     - Checks out the repository
     - Sets up .NET Core 8.0
     - Restores dependencies
     - Builds the project in Release configuration

2. **Unit Test Job**
   - Runs on `ubuntu-latest`
   - Depends on the build job
   - Steps:
     - Checks out the repository
     - Sets up .NET Core 8.0
     - Restores dependencies
     - Runs unit tests

3. **Style Lint Job**
   - Runs on `ubuntu-latest`
   - Depends on the build job
   - Steps:
     - Checks out the repository
     - Installs `dotnet-format`
     - Runs `dotnet format`
     - Installs ESLint and related plugins
     - Runs style lint using ESLint

4. **Security Check Job**
   - Runs on `ubuntu-latest`
   - Depends on the build job
   - Steps:
     - Checks out the repository
     - Sets up .NET Core 8.0
     - Restores dependencies
     - Installs Snyk CLI and authenticates using a secret token
     - Runs Snyk test for security vulnerabilities

#### Continuous Deployment (CD)

The CD process is defined in the `CD.yml` file and is triggered on:
- Push to the `development` branch
- Pull requests targeting the `development` branch

The CD workflow consists of a single job:

1. **Build and Push Job**
   - Runs on `ubuntu-latest`
   - Steps:
     - Checks out the repository
     - Sets up .NET Core 8.0
     - Restores dependencies
     - Builds the project in Release configuration
     - Logs in to Docker Hub using secrets
     - Sets up Docker Buildx
     - Builds the Docker image for the `LawSociety.Server` project
     - Installs Trivy and runs it to scan the Docker image for vulnerabilities
     - Pushes the Docker image to Docker Hub

### License:
This project is licensed under the MIT License.
