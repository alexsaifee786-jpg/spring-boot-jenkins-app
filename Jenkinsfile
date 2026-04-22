pipeline {
    agent any
    stages {
        stage('Pull Code') {
            steps { checkout scm }
        }
        stage('Maven Build') {
            steps {
                // Ye stage code ko compile karke .jar file banayega
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Docker Build & Run') {
            steps {
                // Purana container stop karke naya chalayenge
                sh 'docker stop spring-app || true && docker rm spring-app || true'
                sh 'docker build -t saifee-spring-app .'
                sh 'docker run -d --name spring-app -p 8081:8080 saifee-spring-app'
            }
        }
    }
}
