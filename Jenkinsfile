pipeline {
  agent any
  stages {
    stage('Clone repository') {
      steps {
        git(url: 'https://github.com/kristinadojkoska/Jenkins_DevOps.git', branch: 'master')
      }
    }

    stage('Build image') {
      steps {
        script {
          docker.build("kristinadojkoska/jenkins")
        }

      }
    }

    stage('Push image') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
          }
        }

      }
    }

  }
}