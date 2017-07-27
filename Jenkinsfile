pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        ssh './mvnw -B clean package'
     stash name: 'war', includes: 'target'
      }
     }
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
