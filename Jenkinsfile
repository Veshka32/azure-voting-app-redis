pipeline {
    agent any

    stages {
        stage('Verify branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Long tasks'){
            parallel{
                stage('First check'){
                  steps {
                      sleep(time: 10, unit: 'SECONDS')
                    echo "$WORKSPACE"
                  }  
                }
                stage('Second check'){
                  steps {
                    echo "$STAGE_NAME"
                  }  
                }
            }
        }
    
    }
}
