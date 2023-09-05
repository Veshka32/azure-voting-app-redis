pipeline {
    agent any
    parameters {
        string(name: 'trigger', description: 'yes on no')
    }

    stages {
        stage('Verify branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
         stage('Condition') {
             when {name}
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
