pipeline {
    agent any

    tools {
      nodejs 'NodeJS 4.8.6'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'npm install'
            }
            }

        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'npm test'
            }
        }
        stage('Package') {
            when { branch 'master' }
            steps {
                echo 'Packaging....'
                sh 'npm run package'
            }
        }
    }
}
