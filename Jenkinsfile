pipeline {
    agent any

    environment {
      mvnHome  = tool 'M3'
    }

    stages {   
        stage('Build') {
           steps {
                echo 'Building..'
         
                // Get some code from a GitHub repository
                        git 'https://github.com/jglick/simple-maven-project-with-tests.git'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'

               bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)

            }
        }
        stage('Espera') {
            steps {
                echo 'Esperando..'

//               input "Que quieres comer?"

exit 1

                  archive 'target/*.jar'

            }
        }
    }

        post {
            always {
                echo 'Deploying....'

                   junit '**/target/surefire-reports/TEST-*.xml'
            }
        }

    
}