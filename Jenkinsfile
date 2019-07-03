node {
   stage('Preparation') { 
       // checkout from our repository
      git 'https://github.com/AbrahamCalderon/fleetman-webapp'
   }
   stage('Build') {
      sh 'mvn clean package'
   }
   stage('Results') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.war'
   }
   stage('Deploy') {
      withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        ansiblePlaybook credentialsId: 'SSH-CRED', installation: 'ansible-installation', playbook: 'deploy.yaml', disableHostKeyChecking: true
      }
   }
}
