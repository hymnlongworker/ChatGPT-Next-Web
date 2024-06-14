pipeline {
    agent any

    environment {
        OPENAI_API_KEY = 'ak-JeeF2Dos9tvsqirP6Kx4Xosi0xeDi8KF9QBehp5NVPstckra' // 设置您的实际值
        GOOGLE_API_KEY = '' // 设置您的实际值
        CODE = '' // 设置您的实际值
        BASE_URL = 'https://a.nextapi.fun' // 设置您的实际值
        OPENAI_ORG_ID = '' // 设置您的实际值
        HIDE_USER_API_KEY = '' // 设置您的实际值
        DISABLE_GPT4 = '' // 设置您的实际值
        ENABLE_BALANCE_QUERY = '' // 设置您的实际值
        DISABLE_FAST_LINK = '' // 设置您的实际值
        OPENAI_SB = '' // 设置您的实际值
    }

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

        stage('Print Environment Variables') { // 新添加的阶段
            steps {
                script {
                    // 打印所有环境变量
                    sh 'printenv'
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
