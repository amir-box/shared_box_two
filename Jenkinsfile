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
      script {      
      withCredentials([usernamePassword(credentialsId: 'github-user', passwordVariable: 'GITLABPASS', usernameVariable: 'GITLABUSER')]) {
                            sh "git remote set-url origin http://${GITLABUSER}:${GITLABPASS}@github.com/amir-box/shared_box_two.git"
                            sh "git add ."
                            sh 'git commit -m "version bump"'
                            sh "git push origin HEAD:main"
                        }
    }
      }
    }
    
  }
}
