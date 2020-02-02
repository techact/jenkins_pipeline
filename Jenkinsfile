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
    post {
    failure {
        mail to: 'suresh@ventunotech.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
    }
}
}
