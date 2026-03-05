// Parameterized pipeline
pipeline {
    agent any
    
    tools {
        maven 'Mymaven'
    }
    
    parameters {
        choice(name: 'ENV', choices: ["Dev", "QA"])
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
        }
        
        stage('Build on Dev Env') {
            when {
                expression { params.ENV == 'Dev' }
            }
            steps {
                sh 'mvn compile'
            }
        }
        
        stage('Build on Test Env') {
            when {
                expression { params.ENV == 'QA' }
            }
            steps {
                sh 'mvn test'
            }
        }
    }
}