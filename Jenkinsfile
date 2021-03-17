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
    }
}

def get_target_hosts() {
  if (env.BRANCH_NAME.contains("main")) {
    return ["192.168.10.11", "192.168.10.12"]
  } else if (env.BRANCH_NAME.contains("staging")) {
    return ["192.168.11.11", "192.168.11.12"]
  } else {
    return []
  }
}