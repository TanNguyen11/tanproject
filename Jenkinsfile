pipeline {
    agent { dockerfile true }        
    parameters{
        booleanParam(defaultValue: false, description: '', name: 'runTestSuite')
    }
    stages {
        stage ('Prepare') {
            steps {
                script {
                    if (params.runTestSuite) {
                       //load "jenkins/${params.environment}/env_prop.properties"
                    } else {
                        echo 'no build'
                    }
                }
            }
        }

        stage("Run Automation Testing") {    
            steps {
                
                script {
                    if (params.runTestSuite) {
                       sh 'npm -v'
                       sh 'npm install'
                       sh '$(npm bin)/cypress run'
                    }
                }
            }
        }

         stage('Clean Workspace') {
            steps {
                echo 'Clean Workspace'
                deleteDir()
            }
        }
    }
}