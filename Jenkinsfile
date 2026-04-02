pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    environment {
        NETLIFY_SITE_ID = 'fdbc5129-5749-4373-86de-f60fd1149aff'
        NETLIFY_AUTH_TOKEN = credentials('netlify-token')
    }

    stages {

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'CI=true npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'npm install -g netlify-cli'
                sh 'netlify deploy --prod --dir=build --site=$NETLIFY_SITE_ID --auth=$NETLIFY_AUTH_TOKEN'
            }
        }

    }
}