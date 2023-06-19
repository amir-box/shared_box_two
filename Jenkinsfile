pipeline {
    agent any
    
    stages {

        stage('Test') {
            steps {
                echo 'Completed Testing!'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    def branchName = env.BRANCH_NAME

                   
                        def dockerImageTag = '7.2.1'

                      
                        withCredentials([usernamePassword(credentialsId: 'github-user', passwordVariable: 'GITLABPASS', usernameVariable: 'GITLABUSER')]) {
                            sh "git remote set-url origin http://${GITLABPASS}@github.com/amir-box/shared_box_two.git"
                            sh 'echo hi >> README.md'
                            sh "git add ."
                            sh 'git commit -m "version bump"'
                            sh "git push origin HEAD:main"
                        }

                    
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    def branchName = env.BRANCH_NAME

                    // Check if the branch name is 'main'
                    if (branchName == 'main') {
                        echo "Performing steps for branch ${branchName}"
                    } else {
                        echo "Skipping steps as this is not main branch."
                    }
                }
            }
        }


    }


}
