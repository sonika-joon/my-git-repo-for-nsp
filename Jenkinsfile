pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/sonika-joon/my-git-repo-for-nsp/'
            }
        }

        stage('Build Image') {
            steps {
                sh 'podman build -t nsp-site .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'podman rm -f nsp-site || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'podman run -d -p 8085:80 --name nsp-site nsp-site'
            }
        }

    }
}
