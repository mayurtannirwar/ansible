pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Provision AWS VMs') {
            steps {
                script {
                    sh 'ansible-playbook ansible-tomcat-install-deploy/ansible/provision.yml'
                }
            }
        }

        stage('Configure Tomcat') {
            steps {
                script {
                    sh 'ansible-playbook ansible-tomcat-install-deploy/ansible/configure-tomcat.yml'
                }
            }
        }

        stage('Deploy App') {
            steps {
                script {
                    sh 'ansible-playbook ansible-tomcat-install-deploy/ansible/deploy-app.yml'
                }
            }
        }
    }
}
