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
                expression {
                    // Run if branch name contains the word "feature"
                    env.CURRENT_BRANCH ==~ /.*feature.*/
                }
            }
            steps {
                echo "🚀 Feature branch detected (${env.CURRENT_BRANCH}), running npm install..."
                sh 'npm install'
            }
        }
    }
}

