pipeline {
    agent any
    
    environment {
        // Automatically detect branch name for both job types
        CURRENT_BRANCH = "${env.BRANCH_NAME ?: env.GIT_BRANCH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo "✅ Checked out branch: ${env.CURRENT_BRANCH}"
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



