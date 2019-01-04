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
        sh 'git branch -a'
        echo 'Building'
      }
    }
    stage('Deploy') {
      when{
        branch 'release'
      }
      steps {
        echo 'Deploy'
      }
    }
    stage('PostDeploy') {
      when{
        branch 'release'
      }
      steps {
        echo 'PostDeploy'
      }
    }
  }
}