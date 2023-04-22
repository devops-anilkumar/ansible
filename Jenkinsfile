pipeline{
    agent { label 'ws' }
    environment { 
           ENV_URL = "pipeline.learning.com"  // declaring varibles at pipeline level
           SSH_CREDENTIALS = credentials('SSH_CRED')
        }
    stages{
        stage ('testing the tags'){
            when { expression { env.TAG_NAME == ".*" } }
            steps{
                sh "env"
            }
        }
        stage ('performing lint checks'){
            when { branch pattern: "feature-.*", comparator: "REGEXP"}
            steps{
                sh "env"
                sh "echo this step should run against non-main branches only"
                sh "echo PERFORMING LINT CHECKS"
            }
        } 
        stage ('performing ansible dry run') {   // THIS STAGE SHOULD RUN ONLY AGAINST THE PR
        when { branch pattern: "PR-.*", comparator: "REGEXP"}
        steps{
            sh "env"
            sh "ansible-playbook robot-dryrun.yaml -e COMPONENT=mongodb -e ansible_user=${SSH_CREDENTIALS_USR} -e ansible_password=${SSH_CREDENTIALS_PSW} -e ENV=qa"
          }
       }
       stage ('promotion to prod branch') {      // this branch will run only against the main branch
         when { branch 'main' }
        steps {
            sh "env"
            sh "echo main - PROMOTING TO PROD"
        }
       }
       
    }
}






