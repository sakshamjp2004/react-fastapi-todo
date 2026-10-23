
@Library('todo-shared-library') _

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Files') {
            steps {
                Check_files()
            }
        }

        stage('Build The Image') {
            steps {
                build_image(
                    "shamrock2004",
                    "v1.0.2",
                    "todo-frontend-app",
                    "frontend/."
                )

                build_image(
                    "shamrock2004",
                    "v1.0.2",
                    "todo-backend-app",
                    "backend/."
                )
            }
        }

        stage('Login to DockerHub') {
            steps {
                Login_to_DockerHub()
            }
        }

        stage('Pushing Images to DockerHub') {
            steps {
                push_to_DockerHub(
                    'shamrock2004/todo-frontend-app',
                    'v1.0.2'
                )

                push_to_DockerHub(
                    'shamrock2004/todo-backend-app',
                    'v1.0.2'
                )
            }
        }
    }
}

