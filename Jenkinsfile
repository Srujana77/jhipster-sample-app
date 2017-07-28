pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        ssh './mvnw -B clean package'
     stash name: 'war', includes: 'target'
      }
     }
    stage('Backend') {
   steps {
     parallel(
       'Unit' : {
         unstash 'war'
         sh './mvnw -B test'
         junit '**/surefire-reports/**/*.xml'
        },
        'Performance' : {
          unstash 'war'
          sh './mvnw -B gatling:execute'
       })
       }
      }
    stage('Frontend Test') {
   steps {
     sh 'yarn install'
     sh 'yarn global add gulp-cli'
     sh 'gulp test'
} }
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
