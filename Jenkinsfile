pipeline{
  agent any
  stages{
     stage("Maven Build"){
       steps{
            sh "mvn clean package"
        }
    }
    stage("deploy-dev"){
       steps{
          sshagent(['deploy']) {
            sh "chmod 777 /home/ec2-user/.jenkins -R"
            sh "cp -rp /home/ec2-user/.jenkins/workspace/MCS pipeline/target/*.jar  /home/test/output"
            sh "scp -rp /home/test/output/*.jar test@54.175.214.227:/home/test"
          }
        }
    }
    }
}
