pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/YashinNikita/curl.git'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: env.REPO_URL, branch: 'master'
            }
        }

        stage('Configure and Build') {
            steps {
                sh '''
                    ./buildconf
                    ./configure --with-ssl=/usr/local/opt/openssl
                    make
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    make test
                '''
            }
        }

    }
}
