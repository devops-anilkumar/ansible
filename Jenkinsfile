pipeline{
    agent { label 'ws' }
    environment { 
           ENV_URL = "pipeline.learning.com"  // declaring varibles at pipeline level
           SSH_CREDENTIALS = credentials('SSH_CRED')
        }
    stages{
        stage ('performing lint checks'){
            steps{
                sh "env"
                sh "echo this step should run against non-main branches only"
                sh "echo PERFORMING LINT CHECKS"
            }
        } 
        stage ('performing ansible dry run') {   // THIS STAGE SHOULD RUN ONLY AGAINST THE PR
        steps{
            sh "env"
            sh "ansible-playbook robot-dryrun.yaml -e COMPONENT=mongodb -e ansible_user=${SSH_CREDENTIALS_USR} -e ansible_password=${SSH_CREDENTIALS_PSW} -e ENV=qa"
          }
       }
    }
}
















// pipeline{
//     agent { label 'ws' }
//     environment { 
//            ENV_URL = "pipeline.learning.com"  // declaring varibles at pipeline level
//            SSH_CREDENTIALS = credentials('SSH_CRED')
//         }
//     stages{
//         stage('performing ansible dry run') {   // THIS STAGE SHOULD RUN ONLY AGAINST THE PR
//         steps{
//             sh "env"
//             sh "ansible-playbook robot-dryrun.yaml -e COMPONENT=mongodb -e ansible_user=${SSH_CREDENTIALS_USR} -e ansible_password=${SSH_CREDENTIALS_PSW} -e ENV=qa"
//           }
//        }
//     }
// }