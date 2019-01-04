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
        sh 'git branch'
        // sh 'git checkout master'
        script{
          sh(
              script: 'git rev-parse --abbrev-ref HEAD > curent_branch.txt'
              // returnStdout: true
            )
          def OUTPUT = readFile('curent_branch.txt').trim()
          echo "Current branch $OUTPUT"
        }
          sh 'git checkout master'
          sh "git merge $OUTPUT" 
          sh 'git log'
          sh 'git push origin'
        echo 'PostDeploy'
      }
    }
  }
}