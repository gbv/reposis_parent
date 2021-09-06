pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                    withMaven (maven: 'mvn', jdk: 'OJDK11', mavenLocalRepo: '.repository') {
                      sh "mvn clean install"
                    }
            }
        }

        stage('Clean') {
            steps {
                cleanWs()
            }
        }
    }
}
