pipeline {
    agent any

    stages {
        stage('Clone Project') {
            steps {
                // Cloning the project from GitHub
                git 'https://github.com/YassineGarram/DS-Devops.git'
            }
        }
        stage('Build with Maven') {
            steps {
                // Compiling and building the project with Maven
                sh 'mvn clean install'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    // Analyzing code quality with SonarQube
                    sh 'mvn sonar:sonar -Dsonar.projectKey=StudentDashboard -Dsonar.host.url=http://localhost:9000 -Dsonar.login=your_sonar_token'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                // Building the Docker image
                sh 'docker build -t studentdashboard:latest .'
            }
        }
    }
}
