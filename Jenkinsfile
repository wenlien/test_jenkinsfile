pipeline {
    agent any
    environment {
        MY_HOME = '~/My_HOME'
        PATH = '/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin' 
        MY_STRING = 'hello world!'
    }
    stages {
        stage('check environment') {
            steps {
                echo "${MY_STRING}"
                echo "${MY_HOME}"
                echo env.PATH
                sh 'env'
                sh 'python --version'
                sh 'git --version'
            }
        }
        stage('pull code') {
            steps {
                // git url: 'git@github.com:wenlien/test.git'
                echo 'TBD'
            }
        }
    }
    post {
        always() {
            deleteDir()
        }
        success {
            mail to: "wenlien1001@gmail.com", subject: "SUCCESS: ${currentBuild.fullDisplayName}", body: "Yay, we passed."
        }
        failure {
            mail to: "wenlien1001@gmail.com", subject: "FAILURE: ${currentBuild.fullDisplayName}", body: "Boo, we failed."
        }
    }
}
