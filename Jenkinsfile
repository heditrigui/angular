pipeline{
agent any

        stages{




			    stage('Build docker image'){
                             steps{
                                 script{
                                    sh 'docker build -t heditrigui/angularproject .'
                                 }
                             }
                         }




      stage('Docker login') {

                                         steps {
                                          sh 'echo "login Docker ...."'
                   	sh 'docker login -u heditrigui -p dockerpass'
                               }  }
		 stage('Docker push') {

                 steps {
                      sh 'echo "Docker is pushing ...."'
                     	sh 'docker push heditrigui/angularproject'
                        }  }

                        /*stage('Docker compose') {

                          steps {
                               sh 'docker-compose up -d'
                                 }  }*/


        }
post {
                                                success {
                                                     mail to: "hedi.trigui@esprit.tn",
                                                     subject: "Pipeline Success",
                                                     body: "success on job ${env.JOB_NAME}, Build Number: ${env.BUILD_NUMBER}, Build URL: ${env.BUILD_URL}"
                                                }
                    failure {
                        mail to: "hedi.trigui@esprit.tn",
                         subject: "Pipeline Failure",
                         body: "Failure on job ${env.JOB_NAME}, Build Number: ${env.BUILD_NUMBER}, Build URL: ${env.BUILD_URL} "
                    }
}
      }
