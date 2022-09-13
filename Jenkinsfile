pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps{
                git branch: 'master', url: 'https://github.com/AGS-36/ansible_roles.git'
            }
        }
        stage('Install molecule') {
            steps{
                sh 'cd vector_1; ls; pip3 install -r requirements.txt'
                sh "echo =============="
            }
        }
        stage('Run Molecule'){
            steps{
                sh 'cd vector_1; molecule test'
            }
        }
    }
}
