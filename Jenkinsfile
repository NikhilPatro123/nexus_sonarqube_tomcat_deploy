pipeline {
    agent any

    stages {
        stage('code') {
            steps {
                git 'https://github.com/NikhilPatro123/web-appn.git'
            }
        }
        stage('build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
                environment {
                    scannerHome = tool 'sonar-scanner'
                }
            steps {
                    withSonarQubeEnv('sonarqube') {
                    bat "${scannerHome}/bin/sonar-scanner \
                    -Dsonar.projectKey=mproject1 \
                    -Dsonar.sources=src \
                    -Dsonar.java.binaries=target/classes"
                    }
            }
        }

        stage('artifactory') {
            steps {
              nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'target/myweb-7.9.5.war', type: '.war']], credentialsId: 'nexus-new', groupId: 'in.javahome', nexusUrl: '13.235.241.94:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'app1', version: '7.9.5'
            }
        }
        stage('deploy container'){
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'now-t', path: '', url: 'http://13.235.241.94:8080/')], contextPath: 'web-app', war: 'target/*.war'
            }
        }
    }
}
