pipeline {
    agent any

    stages {
        stage('checkout code from branch22') {
            steps {
                echo 'retrieving code from GIT'
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/boxfuse/boxfuse-sample-java-war-hello.git']])
            }
        }
        stage('build branch22') {
            steps {
                echo 'building the code'
                sh 'mvn clean install'
            }
        }
        stage('Deployment of branch22') {
            steps {
                echo 'Deploying to container'
                deploy adapters: [tomcat8(credentialsId: 'tomcat/tomcat', path: '', url: 'http://172.31.19.81:8088')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
