pipeline {
    agent any
    tools{
        jdk 'jdk11'
        maven 'maven3'
    }
   
    stages {
        stage('Gitcheck Out') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/SurajBele/studentapp.ui.git'
                echo 'Pull sucessfull'
            }
        }
       
        // stage('Compile') {
        //     steps {
        //         sh 'mvn clean package -DskipTests=true'
        //         echo 'Build sucessfull'
        //     }
        // }
       
        // stage('Sonar Analysis') {
        //     steps {
        //         script{
        //                  withSonarQubeEnv(credentialsId: 'Sonar')
        //             {
        //                sh 'mvn sonar:sonar'
        //                echo ' Test sucessfull'
        //             }
        //         }
        //     }
        // }
       
        // stage("Quality Gate"){
        //    steps {
        //         script {
        //             waitForQualityGate abortPipeline: false, credentialsId: 'Sonar'
        //             echo ' Quality Gate test sucessfull'
        //         }
        //     }
        // }
       
        // stage ('Deploy') {
        //     steps {
        //         deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.89.37.154:8080/')], contextPath: '/', war: '**/*.war'
        //         echo ' Deploy sucessfull'
        //     }
        // }
    }
}
