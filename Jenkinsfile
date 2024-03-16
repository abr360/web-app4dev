pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 sh "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '2b055013-bd24-49d7-a1a6-3965f362853e', path: '', url: 'http://192.168.1.4:8090')], contextPath: '/cicd-web-app', war: '**/*.war'
 }
 }
 }
}
