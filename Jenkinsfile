pipeline {
    agent any
    tools{
           maven "maven"
    }
    stages {
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
