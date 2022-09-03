pipeline {
    agent any
    stages {
        stage('pull the code from SCM'){
            steps {
                echo 'connecting to github and pulling the code..'
                git branch: 'monolith-app-deployment',
                url: 'https://github.com/Narsi-Myteaching/morning-devops-01.git'
                echo 'source code pulling completed'
            }
        }
        stage('copying the k8s manifest files to k8s master'){
            steps{
                echo 'copying the k8s manifest files to k8s master'
                sshagent(['Ansible-Server-Machine']) {
                    sh 'scp dev-applications/** ansible-admin@172.31.28.198:/opt/app-files'
                    sh 'scp dev-database/** ansible-admin@172.31.28.198:/opt/app-files'
                    
                    sh '''
                     ssh -tt ansible-admin@172.31.28.198 << EOF
                     ansible-playbook  /opt/app-files/k8s-files-download-playbook.yml   
                     ansible-playbook  /opt/app-files/medilab-db-deploy-cleanup-playbook.yml
                     ansible-playbook  /opt/app-files/medilab-db-deploy-playbook.yml
                     ansible-playbook  /opt/app-files/medilab-app-deploy-cleanup-playbook.yml
                     ansible-playbook  /opt/app-files/medilab-app-deploy-playbook.yml
                     exit
                     EOF
                    '''
                }
            }
        }

        
    }
}
