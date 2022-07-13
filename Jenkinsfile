pipeline {
    agent any
    environment {

//PATH = "/opt/apache-maven-3.8.6/bin/:$PATH"

//PATH = "/opt/gradle/gradle-7.5-rc-4/bin/:$PATH"

    PATH = "/opt/gradle/gradle-7.4.2:$PATH"

   }



     options {

        timestamps()

    }

    stages {
        stage ("Clone Repository") {
                steps {
                   git branch: 'master', url: 'https://github.com/Swadhin1997/hakunamatata.git'
                }
            }  

            stage('Prep') {
            steps {
                script {
                    GIT_BRANCH=sh(returnStdout: true, script: 'git symbolic-ref --short HEAD').trim()
                    currentBuild.setDisplayName("#${currentBuild.number} [" + GIT_BRANCH + "]")
                    sh "export GIT_BRANCH=$GIT_BRANCH"
                }
            }
        }  
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage ('Building Apk') {
            steps {
              
               echo "Building"
            }   
            
            }
  stage('Quality Analysis') {
            parallel {
                // run Sonar Scan and Integration tests in parallel. 
                stage('Integration Test') {
                    steps {
                        echo 'Run integration tests here...'
                    }
                }

        stage ('Declarative Post Options') {
            steps {
                script {
                    echo 'Sending Post Build Notifications'
                }
            }   
            
            }
    }
}
    }
} 
