pipeline {

  agent {
    label 'jenkins-agents'
  }

  triggers {
    pollSCM '* * * * *'
  }

  stages {
   
    stage ('scm-checkout'){
      steps {
        checkout scmGit(branches: [[name: '*/feat01']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-creds-navya', url: 'https://github.com/navya0727/mavenrepo.git']])
        sh ' echo "myfirstpipeline" '
       }
    
   }
   
   stage ('mvn-build'){
     steps {
       sh ' mvn package '

    }


   } 
    


  }      //all stages complete here
   
}       // pipeline completes here
