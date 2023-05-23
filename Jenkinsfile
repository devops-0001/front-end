pipeline {
  agent none
  stages {
    stage('Build') {
      agent {
        docker {
          image 'node:4-alpine'
        }

      }
      steps {
        echo 'Building..'
        sh 'npm install'
      }
    }

    stage('Test') {
      agent {
        docker {
          image 'node:4-alpine'
        }

      }
      steps {
        echo 'Testing..'
        sh 'npm install'
        sh 'npm test'
      }
    }

    stage('Package') {
      agent any
      when {
        branch 'master'
      }
      steps {
        echo 'Packaging....'
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
            def dockerImage = docker.build("initcron/frontend:v${env.BUILD_ID}", "./")
            dockerImage.push()
            dockerImage.push("latest")
          }
        }

      }
    }

  }
  tools {
    nodejs 'NodeJS 4.8.6'
  }
}
