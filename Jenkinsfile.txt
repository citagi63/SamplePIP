pipeline {
    agent any
    tools {
  maven 'maven'
}
    stages {
        stage('mvn builds') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('agent linux'){
            agent {label 'linux_server'}
        steps {
          sh 'mvn clean package'
        } 
        }
    }
}

