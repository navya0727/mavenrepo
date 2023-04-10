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
        sh 'cat Jenkinsfile'
       }
    
    }


  }      //all stages complete here
   
}       // pipeline completes here
