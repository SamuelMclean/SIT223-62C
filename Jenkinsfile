pipeline {
    agent any
    
    environment {
        DIRECTORY_PATH = 'path to directory of code being fetched'
        TESTING_ENVIROMENT = '51P_TEST'
        PRODUCTION_ENVIROMENT = '51P_PROD'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Build Via CMake'
            }
        }
        stage('Unit and integration Tests') {
            steps {
                echo 'testing via Selenium'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Code check Via PMD'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Security check via Fortify'
                always{
                    mail to: "spudoto@gmail.com",
                    subject: "Security Check Completed",
                    body: "Security Check Completed Successfully"
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Deploy to microsoft azure test enviroment'
            }
        }
        stage('Deploy on Production') {
            steps {
                echo 'Deploy to microsoft azure production enviroment'
            }
        }
        post
        {
            success{
                mail to: "spudoto@gmail.com",
                subject: "Jenkins Build Post Report",
                body: "Build completed Successfully"
            }
            failure{
                mail to: "spudoto@gmail.com",
                subject: "Jenkins Build Post Report",
                body: "Build Failed"
            }
        }
    }
}
