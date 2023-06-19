pipeline {
  agent any

  stages {

    stage('Make file changes') {
      steps {
        script {
            def dockerImageTag = '7.2.1'
            sh 'chmod +x increase_tag'
          sh "./increase_tag ${dockerImageTag}"
        }
      }
    }

    stage('Commit and push changes') {
      steps {
        git credentialsId: 'github-user', url: 'https://github.com/amir-box/shared_box_two.git'
        sh 'git add .'
        sh 'git commit -m "Jenkins pipeline commit"'
        sh 'git push'
      }
    }
  }
}
