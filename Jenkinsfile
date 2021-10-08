pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                    withMaven (maven: 'mvn', jdk: 'OJDK11') {
                        withCredentials([usernamePassword(credentialsId: 'gpg', passwordVariable: 'KEYPW_VAR', usernameVariable: 'KEYID_VAR')])
                        {
                            sh 'mvn clean install -Dgpg.executable=gpg -Dgpg.keyname=${KEYID_VAR} -Dgpg.passphrase=${KEYPW_VAR}'
                        }
                    }
            }
        }

        stage('Deploy') {
            steps {
                    withMaven (maven: 'mvn', jdk: 'OJDK11', mavenSettingsConfig: 'maven-deploy-settings') {
                        withCredentials([
                        usernamePassword(credentialsId: 'ossrhs01', passwordVariable: 'PASSWORD_VAR', usernameVariable: 'USERNAME_VAR'),
                        usernamePassword(credentialsId: 'gpg', passwordVariable: 'KEYPW_VAR', usernameVariable: 'KEYID_VAR')
                        ])
                        {
                            sh 'mvn deploy -Dgpg.executable=gpg -Dgpg.keyname=${KEYID_VAR} -Dgpg.passphrase=${KEYPW_VAR} -Dossrhs01.username=${USERNAME_VAR} -Dossrhs01.password=${PASSWORD_VAR}'
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
