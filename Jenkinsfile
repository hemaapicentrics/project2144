pipeline {
     agent any
         stages {
             stage('Build') {
                 steps {
                     echo 'Application is in Building Phase'
                     bat 'mvn clean install'
                     }
                 }
             stage('Test') {
                 steps {
                     echo 'Application is in Testing Phase'
                     bat 'mvn test'
                       }
                 }
                 stage('Deploy to Cloudhub') { 
                   environment {
                                 ANYPOINT_CREDENTIALS = credentials('hema-feb13')
                               }
                   steps {
                            bat 'mvn package deploy -DmuleDeploy -DmuleVersion=4.3.0 -Dusername=hema-feb13 -Dpassword=Hemala03 -DworkerType=Micro -Dworkers=1 -Dregion=us-west-2'
                         }
                    }
         }
     }