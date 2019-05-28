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

   //               archive 'target/*.jar'

            }
        }
    }

     post {
         always {
             echo 'Deploying....'

          //      junit '**/target/surefire-reports/TEST-*.xml'

          echo "La duracion del job '${JOB_NAME}' ha sido ${currentBuild.duration} ms"
         }

         failure {

             echo 'Mail cuando da error....'

            mail to: 'elenanp@meta4.com',
            subject: "La has liado en el Pipeline: ${currentBuild.fullDisplayName}",
            body: "Que tienes muñones en vez de manos, vete a ${env.BUILD_URL}" 
         }

         changed {

             echo 'Mail cuando cambia estado....'

            mail to: 'aitorg@meta4.com',
            subject: "La has liado pero no siempre en el Pipeline: ${currentBuild.fullDisplayName}",
            body: "Que se puede hacer?, vete a ${env.BUILD_URL}" 

         }

     }


}