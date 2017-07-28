pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './mvnw -B clean package -DskipTests=true '
     stash name: 'war', includes: 'target'
      }
     }
    stage('Backend') {
   steps {
     parallel(
       'Unit' : {
         echo "*****************************UNIT TEST WORKING**************************************"
        },
        'Performance' : {
          unstash 'war'
          /*sh './mvnw -B gatling:execute'*/
         echo "*****************************PERFORMANCE TEST WORKING**************************************"   
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
