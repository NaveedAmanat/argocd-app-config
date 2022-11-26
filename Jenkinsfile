pipeline{
    agent any
    stages{
        stage('Update Manifest'){
            steps{
                script{
                    withCredentials([usernamePassword(credentialsId: 'Github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh "git config user.email mnaveed0004@gmail.com"
                        sh "git config user.name NaveedAmanat"
                        sh 'cd dev'
                        sh "sed -i 's+naveed0004/spring-integration.*+naveed0004/spring-integration:${IMAGE_TAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git status"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest:v${BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/argocd-app-config.git HEAD:main"
                 }
            }
        }
        }
    }
}
