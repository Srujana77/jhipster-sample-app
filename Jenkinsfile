pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Jenkins Minute Pipeline'
        input(message: 'Hello?', ok: 'Works!')
        echo 'Hello'
        sh 'echo Build'
      }
    }
    stage('Backend') {
      steps {
        parallel(
          "Unit": {
            sh 'echo Unit'
            
          },
          "Performance": {
            sh 'echo Performance'
            
          }
        )
      }
    }
    stage('Frontend') {
      steps {
        sh 'echo Frontend'
      }
    }
    stage('Static Analysis') {
      steps {
        sh 'echo Static Analysis'
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo Deploy'
      }
    }
  }
}