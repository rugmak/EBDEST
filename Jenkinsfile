pipeline {
    agent any
    triggers {
        githubPush()
    }
    
stages {
        stage('Create and Push Mirror repo') {
            steps {
                withCredentials([gitUsernamePassword(credentialsId: 'EBSOURCE', gitToolName: 'Default'), gitUsernamePassword(credentialsId: 'EBDEST', gitToolName: 'Default')]) {
                sh '''
                rm -rf EBSYNC.git || true
                git clone --bare https://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@gitext.elektrobitautomotive.com/ruk273132/EBSYNC.git
                ls
                cd  /var/jenkins_home/workspace/EB-PERJOB/EBSYNC.git/
                git remote set-url --push origin https://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@github.com/rugmak/EBDEST.git
                git remote -v
                git fetch -p origin
                ls
                git push --mirror --force https://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@github.com/rugmak/EBDEST.git
                '''
                }
                }
            }
        stage('Clear Workspace') {
            steps {
                sh 'pwd'
                sh 'ls -l'
                deleteDir()
            }
                
        }    
    }
}
