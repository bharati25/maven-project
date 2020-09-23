pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/bpatil25/maven-project'
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
        stage ('deploy to dev') {
             steps {
                  sshagent(['9de4f73e-b9f0-4e4b-aec0-d52203fda3e2']) {
                  sh 'scp -o StrictHostKeyChecking=no  /var/lib/jenkins/workspace/my-first-job/webapp/target/*.war ec2-user@172.31.39.173:/var/lib/tomcat/webapps'
} } }

         
}
}
