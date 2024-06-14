pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // 拉取代码
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // 构建 Docker 镜像
                    sh 'docker build -t yidadaa/chatgpt-next-web .'
                }
            }
        }

        stage('Run Docker Compose') {
            steps {
                script {
                    // 运行 Docker Compose
                    sh 'docker-compose up -d'
                }
            }
        }
    }

    post {
        always {
            // 清理构建环境
            sh 'docker-compose down'
        }
        success {
            // 构建成功时的操作，例如发送通知
            echo 'Build and deployment successful.'
        }
        failure {
            // 构建失败时的操作，例如发送通知
            echo 'Build and deployment failed.'
        }
    }
}
