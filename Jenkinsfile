pipeline {
    agent any
    
    stages {
        stage('Hello') {
            environment {
                TARGET_HOST = "192.168.2.11"
            }
            steps {
                echo "Hello World - ${env.TARGET_HOST}"
                echo "branch: ${BRANCH_NAME}"
                echo 'tag: ${TAG_NAME}'
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
        stage('main') {
            when { branch 'main' }
            steps {
                script {
                    def target_hosts = get_target_hosts()
                    for (TARGET_HOST in target_hosts) {
                        echo "main - ${TARGET_HOST}"
                    }
                }
            }
        }
        stage('staging') {
            when { branch 'staging' }
            steps {
                script {
                    def target_hosts = get_target_hosts()
                    for (TARGET_HOST in target_hosts) {
                        echo "staging - ${TARGET_HOST}"
                    }
                }
            }
        }
        stage('dev') {
            when { branch 'dev' }
            steps {
                script {
                    def target_hosts = get_target_hosts()
                    for (TARGET_HOST in target_hosts) {
                        echo "dev - ${TARGET_HOST}"
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def target_hosts = get_target_hosts()
                    for (TARGET_HOST in target_hosts) {
                        echo "deploy - ${TARGET_HOST}"
                    }
                }
            }
        }
    }
}

def get_target_hosts() {
  if (env.BRANCH_NAME.contains("main")) {
    return ["192.168.11.11", "192.168.11.22", "192.168.11.33"]
  } else if (env.BRANCH_NAME.contains("staging")) {
    return ["192.168.22.22"]
  } else if (env.BRANCH_NAME.contains("dev")) {
    return ["192.168.33.33"]
  } else {
    return []
  }
}
