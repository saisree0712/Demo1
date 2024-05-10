pipeline {
agent any
stages {
stage('Checkout') {
steps {
// Checkout code from Git repository
checkout scmGit(branches: [[name: '*/main']], extensions: [],
userRemoteConfigs: [[credentialsId: 'c582966d-0b1f-42cc-bf39-6b73dccc54b8', url: 'https://github.com/saisree0712/Demo1']])
}
}
stage('Build and Compile') {
steps {
// Use Maven to build and compile the project
sh 'mvn clean compile'
}
post {
success {
// If build succeeds, archive the build artifacts
archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
}
failure {
// If build fails, send a notification or take other actions
echo 'Build failed! Please check the build logs.'
}
}
}
}
// Post-build actions (optional)
post {
always {
// Clean up workspace after the build is complete
cleanWs()
}
}
}
