pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/reyazmansoori04/jenkins-example'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn install'
                }
            }
        }

         stage ('deploy to tomcat') {
             steps {
             sshagent(['tomcatt']) {
  sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@ip-172.31.37.6:/var/lib/tomcat/webapps'

      }
             }
   }
}
}
