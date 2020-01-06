pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        sh './gradlew clean build'
      }
    }

    stage('Deploy') {
      steps {
        script {
          docker.build('panda-be')
          docker.withRegistry('https://955095959256.dkr.ecr.cn-northwest-1.amazonaws.com.cn', 'ecr:cn-northwest-1:panda-ecr') {
            docker.image('panda-be').push('latest')
          }
        }
      }
    }

  }
}