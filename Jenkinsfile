pipeline {
    agent any
    stages {
        stage('Download repo') {
            steps {
                git branch: 'main', credentialsId: 'ec80c052-50b3-40c3-b45b-fa5da763dd6d', url: 'git@github.com:Owirtifo/filebeat-molecule.git'
            }
        }
        stage('Download role') {
            steps {
                sh 'ansible-galaxy role install -r requirements.yml --force'
            }
        }
        stage('Install molecule') {
            steps {
                sh 'pip3 install --user "molecule" "molecule_docker"'
            }
        }
        stage('Run test') {
            steps {
                sh 'molecule test -s easy'
            }
        }
    }
}