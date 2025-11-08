pipeline {
    agent any

    stages {

         stage('Set Branch Name') {
            steps {
                script {
                    env.BRANCH_NAME = sh(script: "git rev-parse --abbrev-ref HEAD", returnStdout: true).trim()
                    echo "Current branch is: ${env.BRANCH_NAME}"
                }
            }
        }
        
        // stage('Checkout') {
        //     when {
        //         expression { env.BRANCH_NAME ==~ /.*feature.*/ }
        //     }
        //     steps {
        //         git branch: 'feature',
        //             url: 'https://github.com/terra-git/simplenode.git'
        //     }
        // }

        stage('Install Dependencies') {
            when {
                expression { env.BRANCH_NAME ==~ /.*feature.*/ }
            }
            steps {
                echo "Feature branch detected via webhook, running npm install..."
                sh 'npm install'
            }
        }
    }
}



