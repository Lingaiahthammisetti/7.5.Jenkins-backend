pipeline {
    agent {
            label 'AGENT-1'
         }
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 30, unit: 'MINUTES')
       //  disableConcurrentBuilds()
         ansiColor('xterm')
    }
    //  parameters {
    //    choice(name: 'action', choices: ['Apply', 'Destroy'], description: 'Pick something')
    //  }
    stages {
        stage('NPM Dependencies') { 
            steps {
                sh """
                  npm install
                  ls -ltr
                  
                """ 
            }
        }
    }
     post { 
        always { 
            deleteDir()
            echo 'I will always say Hello Always!'
        }
        success { 
            echo 'I will always say Hello Success!'
        }
        failure{ 
            echo 'I will always say Hello failure!'
        } 
    }
}
