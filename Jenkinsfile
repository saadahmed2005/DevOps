pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/saadahmed2005/DevOps.git'
            }
        }

        stage('Build') {
            steps {
                bat """
                javac Factorial.java
                """
            }
        }

        stage('Run') {
            steps {
                bat """
                java Factorial
                """
            }
        }

        stage('Deploy') {
            steps {
                bat """
                if not exist deployments mkdir deployments
                copy Factorial.class deployments\\
                """
            }
        }
    }

    post {

        success {
            echo "Build, Test, and Deployment completed successfully."
        }

        failure {
            echo "Pipeline failed."
        }

        always {
            echo "Pipeline execution finished."
        }
    }
}
