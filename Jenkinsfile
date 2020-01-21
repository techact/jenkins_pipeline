pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "${A}"'
                sh 'echo "${B}"'
                sh 'echo "${C}"'
                sh 'echo "${D}"'
                sh 'echo "${E}"'
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
    }
}
