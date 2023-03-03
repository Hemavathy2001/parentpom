pipeline {
    agent any
    tools{
           maven "maven"
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn compile -s settings.xml'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test -s settings.xml'
            }
        }
        stage ('deploy'){     
            steps{
                withCredentials([usernamePassword(credentialsId: 'git', passwordVariable: 'PASSWORD_VAR', usernameVariable: 'USERNAME_VAR')])
                {
                    sh 'mvn deploy -s settings.xml -Dserver.username=${USERNAME_VAR} -Dserver.password=${PASSWORD_VAR}'
                }
            }
        }
    }
}
