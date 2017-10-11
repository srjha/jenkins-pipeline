pipeline {
    agent { label 'master' }
    stages {
       stage('build') {
          steps {
             bat 'gradle clean build'
             echo 'Build done'
          }
       }
    }
}
