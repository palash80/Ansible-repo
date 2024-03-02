pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/palash80/Ansible-repo.git'   
        // INSTALL_WORKSPACE = "/var/lib/jenkins/workspace/Ansible-repo"
    }

    stages {
        stage('Clone Repository') {
            steps {
                cleanWs()
                sh "ls"
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: "${REPO_URL}"]]])
                sh "pwd"
                sh "ls"
                echo "${WORKSPACE}"
            }
        }

        stage('List Active private Servers') {
            steps {
                
                sh "pwd"
                sh "ls"
                echo "${env.INSTALL_WORKSPACE}"
                sh "ansible-inventory --graph -i ${WORKSPACE}/aws_ec2.yml"
                // -i ${env.INSTALL_WORKSPACE}/aws_ec2.yml"
            }
        }

        stage('Install Posgresl') {
            steps {
                sh "ansible-playbook -i ${WORKSPACE}/aws_ec2.yml ${WORKSPACE}/psql.yml" 
            }
            
            post {
                success {
                    echo 'Succeeded!'
                }
                failure {
                    echo 'Failed!'
                }
            }
        }
    }
}
