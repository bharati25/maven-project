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
                  sshagent(['db1a4e4d-2ffc-4d7c-9c6e-a6e014e6237a']) {
                  sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.39.173:/var/lib/tomcat/webapps'
} } }

         
}
}
