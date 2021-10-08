pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                    withMaven (maven: 'mvn', jdk: 'OJDK11') {
                      sh "mvn clean install"
                    }
            }
        }

        stage('Deploy') {
            steps {
                    withMaven (maven: 'mvn', jdk: 'OJDK11', mavenSettingsConfig: 'maven-deploy-settings') {
                        withCredentials([usernamePassword(credentialsId: 'ossrhs01', passwordVariable: 'PASSWORD_VAR', usernameVariable: 'USERNAME_VAR')])
                        {
                            sh "mvn deploy -Dossrhs01.username=${USERNAME_VAR} -Dossrhs01.password=${PASSWORD_VAR}"
                        }
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
