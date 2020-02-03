pipeline {
    agent any
    
    environment {
        secret = credentials('SECRET_TEXT')
        AWS_ACCESS_KEY = "AXXXXXXX"
        AWS_SECRET_KEY = "SXXXXXXX"
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'echo ${MY_GLOBAL_VAR}'
                sh 'echo $secret'
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
                    date
                '''
            	}
            	retry(3) {
                    sh './flakey-deploy.sh'
                }

                timeout(time: 3, unit: 'MINUTES') {
                    sh './health-check.sh'
                }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
                timeout(time: 3, unit: 'MINUTES') {
                    retry(5) {
                        sh './flakey-deploy.sh'
                    }
                 }
            }
        }
    }
    post {
        always {
            echo 'I will always get executed :D'
        }
        success {
            echo 'I will only get executed if this success'
        }
        failure {
            echo 'I will only get executed if this fails'
            mail to: 'suresh@ventunotech.com',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is wrong with ${env.BUILD_URL}"
        }
        unstable {
            echo 'I will only get executed if this is unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
}
}
