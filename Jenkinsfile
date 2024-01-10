pipeline {
    agent any
    tools{
        // Tools configuration add here
        jdk 'jdk11'
        maven 'maven3'
    }
   
    stages {
        stage('Gitcheck Out') {
            // Add here github source code URL
            steps {
                git changelog: false, poll: false, url: 'https://github.com/aakashbshendage/Student_App.git'
                echo 'Pull sucessfull'
            }
        }
       
        stage('Compile') {
            // Add here building stage
            steps {
                sh 'mvn clean package -DskipTests=true'
                echo 'Build sucessfull'
            }
        }
       
        stage('Sonar Analysis') {
            // Add here sonarqube configuration
            steps {
                script{
                         withSonarQubeEnv(credentialsId: 'sonar')
                    {
                       sh 'mvn sonar:sonar'
                       echo ' Test sucessfull'
                    }
                }
            }
        }
       
        stage("Quality Gate"){
            // Add here Quality Gate stage
           steps {
                script {
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonar'
                    echo ' Quality Gate test sucessfull'
                }
            }
         }
       
        // stage ('Deploy') {
        //     steps {
        //         deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.89.37.154:8080/')], contextPath: '/', war: '**/*.war'
        //         echo ' Deploy sucessfull'
        //     }
        // }
    }
}
