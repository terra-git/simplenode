pipeline {
    agent any

    stages {
        stage('Checkout') {
            when {
                expression { env.BRANCH_NAME ==~ /.*feature.*/ }
            }
            steps {
                git branch: 'feature',
                    url: 'https://github.com/terra-git/simplenode.git'
            }
        }

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



