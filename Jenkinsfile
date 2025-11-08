pipeline {
   // agent { label 'node-agent' }
   agent any
    stages {
        stage('Checkout') {
            when {
                branch 'feature'
            }
            steps {
                git branch: 'feature',
                    url: 'https://github.com/terra-git/simplenode.git'
            }
        }

        stage('Install Dependencies') {
            when {
                branch 'feature'
            }
            steps {
                echo "Feature branch detected via webhook, running npm install..."
                sh 'npm install'
            }
        }
    }
}
