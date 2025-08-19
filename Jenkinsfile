pipeline {
    agent any

    stages {
        stage('Clonar código') {
            steps {
                git branch: 'main', url: 'https://github.com/gyovanesouzza/api-flash.git'
            }
        }

        stage('Build Docker') {
            steps {
                sh 'docker build -t api-flash .'
            }
        }


        stage('Parar container antigo') {
            steps {
                sh 'docker stop api-flash || true && docker rm api-flash || true'
            }
        }

        stage('Rodar novo container') {
            steps {
                sh 'docker run -d --name api-flash -p 5000:5000 api-flash'
            }
        }
    }
}
