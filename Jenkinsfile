pipeline {
    agent any

    stages {
        stage('Hello') {
            environment {
                TARGET_HOST = "192.168.2.11"
            }
            steps {
                echo "Hello World - ${env.TARGET_HOST}"
            }
        }
        stage('World') {
            environment {
                TARGET_HOST = "192.168.2.22"
            }
            steps {
                echo "Hello World - ${TARGET_HOST}"
            }
        }
    }
}
