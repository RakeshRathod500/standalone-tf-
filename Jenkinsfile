pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-access-key-id')  // Replace with Jenkins credential ID
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')  // Replace with Jenkins credential ID
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: ''  // Replace with your repo URL
            }
        }

        stage('Terraform Init') {
            steps {
                bat 'terraform init'
            }
        }

        stage('Terraform Validate') {
            steps {
                bat 'terraform validate'
            }
        }

        stage('Terraform Plan') {
            steps {
                bat 'terraform plan'
            }
        }
    }

    post {
        success {
            echo 'Terraform plan executed successfully!'
        }
        failure {
            echo 'Terraform plan failed!'
        }
    }
}
