pipeline {
    agent any

    environment {
      mvnHome  = tool 'M3'
    }

    stages {   
        stage('Build') {
           steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}