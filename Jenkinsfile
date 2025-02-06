pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git url: https://github.com/Jeng2004/my-html-project.git
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    def studentId = "66022994" // แทนที่ด้วยรหัสนิสิตของคุณ
                    dockerImage = docker.build("my-html-project:${env.BUILD_NUMBER}-${studentId}")
                }
            }
        }

        stage('Deploy to Docker') {
            steps {
                script {
                    // รัน Docker container ตาม port ที่กำหนด (เช่น 3000)
                    dockerImage.run('-p 3000:80') // เปลี่ยนพอร์ตตามความต้องการ
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
