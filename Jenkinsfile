node {
   stage('Preparation') { 
       // checkout from our repository
      git 'https://github.com/AbrahamCalderon/fleetman-webapp'
   }
   stage('Build') {
      sh 'mvn package'
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
}
