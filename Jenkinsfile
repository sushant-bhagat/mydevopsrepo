// Parameterized pipeline
pipeline {
    agent any
    
    tools {
        maven 'mymaven'
    }
    
    parameters {
        choice(name: 'ENV', choices: ["","Dev", "QA"])
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sushant-bhagat/mydevopsrepo.git'
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
