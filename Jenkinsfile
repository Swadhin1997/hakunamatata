pipeline {
   // environment {
    //  PATH = "/opt/maven/bin/:$PATH"
   //   PATH = "/opt/gradle/gradle-7.4.2/bin/:$PATH"
    //  JAVA_TOOL_OPTIONS = "-Duser.home=/opt/maven"
   // }
agent any 
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
    
        stage ('Building file') {
            steps {
              
               echo "Building file"
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

