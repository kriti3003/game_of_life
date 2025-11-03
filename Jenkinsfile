pipeline {
    agent any

    tools {
        maven 'Maven'       // Make sure Maven is configured under "Global Tool Configuration"
        jdk 'JDK17'         // Use your installed JDK
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/wakaleo/game-of-life.git'
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Build & Unit Test') {
            steps {
                sh 'mvn test'
                sh 'mvn package'
            }
        }

        stage('SonarQube Analysis') {
            when {
                expression { return false } // change to true if you integrate SonarQube
            }
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Deploy to Server') {
            steps {
                echo 'Deploying to Jetty...'
                sh 'mvn jetty:run &'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Deployment successful!'
        }
        failure {
            echo '❌ Build failed. Please check logs.'
        }
    }
}
