pipeline {
  agent any
  stages {
    stage('Testing') {
      steps {
        echo 'Testing...'
      }
    }
    stage('Building') {
      steps {
        echo 'Building'
      }
    }
    stage('Deploy') {
      when{
        branch "*release*"
      }
      steps {
        echo 'Deploy'
      }
    }
    stage('PostDeploy') {
      when{
        branch "*release*"
      }
      steps {
        sh 'git status'
        sh 'git checkout master'
        script{
          def BRANCH = sh(
              script: 'git rev-parse --abbrev-ref HEAD'
              returnStdout: true
            ).trim()
          echo "Current branch $BRANCH"
        }
        // sh 'git merge 
        echo 'PostDeploy'
      }
    }
  }
}