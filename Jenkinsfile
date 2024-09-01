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
    environment {
        def appVersion = '' //variable declaration here.
    }
    stages {
        stage('read the version') {
            steps {
                script {
                def packageJson = readJSON file: 'package.json'
                appVersion = packageJson.version
                echo "application version: $appVersion"
            }
            }
        }
        stage('NPM Dependencies') { 
            steps {
                sh """
                  npm install
                  ls -ltr
                  echo "application version: $appVersion"
                  
                """ 
            }
        }
         stage('Build') { 
            steps {
                sh """
                  zip -r backend-${appVersion}.zip * -x Jenkinsfile -x backend-${appVersion}.zip
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
