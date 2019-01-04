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
        // sh 'git merge '
        echo 'PostDeploy'
      }
    }
  }
}