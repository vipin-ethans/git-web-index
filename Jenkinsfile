pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'master', url: 'https://github.com/vipin-ethans/git-web-index.git'
            }
        }

        stage('Deploy to Web Server') {
            steps {
                sshagent (credentials: ['web-server-ssh-key']) {
                    sh '''
                        scp -o StrictHostKeyChecking=no index.html ec2-user@13.233.223.119:/tmp/
                        ssh -o StrictHostKeyChecking=no ec2-user@13.233.223.119 'sudo mv /tmp/index.html /var/www/html/'
                        
                    '''
                }
            }
        }
    }
}
