pipeline {
  agent any
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
      when {
        branch 'master'
      }
      steps {
        echo 'Packaging....'
        sh 'npm run package'
        archiveArtifacts '**/distribution/*.zip'
      }
    }

    stage('Demo') {
      steps {
        sleep 5
      }
    }

  }
  tools {
    nodejs 'NodeJS 4.8.6'
  }
}