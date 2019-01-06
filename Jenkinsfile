pipeline {
  agent any
  parameters {
          booleanParam(defaultValue: false, description: 'Activate PostDeploy process :merging to master and develop, delete release branch', name: 'PostDeploy')
      }
  stages {
    stage('Testing') {
      steps {
        echo "${env.JOB_NAME}"
        echo "${env.GIT_BRANCH}"
        echo "${env.GIT_URL}"
        echo "${env.GIT_COMMIT}"
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
        branch "release*"
      }
      steps {
        echo 'Deploy'
      }
    }
    stage('PostDeploy') {
      when{
        allOf{
        branch "release*"
        expression{return params.PostDeploy}
        
        }
      }
      steps {
        sh 'git fetch'
        sh 'git status'
        sh 'git branch -a'
        sh 'pwd'
        script{
          sh(
              script: 'git rev-parse --abbrev-ref HEAD > curent_branch.txt'
            )
          def OUTPUT = readFile('curent_branch.txt').trim()
          sh "githalper.sh $OUTPUT ${env.JOB_NAME}"
          echo "Current branch $OUTPUT ${env.JOB_NAME}"
        }
        echo 'PostDeploy'
      }
    }
  }
}