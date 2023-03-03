pipeline {
    agent any
    tools{
           maven "maven"
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version;mvn clean install'
                sh 'mvn compile'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test'
            }
        }
        stage ('deploy'){     
            steps{
                withCredentials([usernamePassword(credentialsId: 'git', passwordVariable: 'PASSWORD_VAR', usernameVariable: 'USERNAME_VAR')])
                {
                    sh 'mvn deploy -s .m2/settings.xml -Dserver.username=${USERNAME_VAR} -Dserver.password=${PASSWORD_VAR}'
                }
            }
        }
    }
}