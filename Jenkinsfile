pipeline {
    agent any

    stages {
        stage('Verify branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Docker build'){
            steps{
                powershell(script: 'docker images -a')
                powershell(script: """
                    cd azure-vote
                    docker images -a
                    docker build -t jenkins-pipeline .
                    docker images -a
                    cd ..
                """)
            }
        }
        stage('Start test app'){
            steps {
                powershell(script: """
                    docker-compose up -d
                   
                """)
            }
            post{
                success{
                    echo 'Started OK'
                }
                failure{
                    echo 'Start failed'
                }
            }
        }
        stage('Long tasks'){
            parallel{
                stage('First check'){
                  steps {
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
