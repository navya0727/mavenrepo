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
        sh ' echo "myfirstpipeline"'
       }
   } //scm stage closed
   

   stage ('mvn-build'){
     steps {
       sh ' mvn package '

    }

   } //build stage completes here
    

   stage ('code quality'){
     steps {
        withSonarQubeEnv(credentialsId: 'jenkins-sonar-global-token', installationName: 'sonar-server' ) 
       sh ' mvn sonar:sonar '

    }

   } //sonar stage completes here 

   

    stage ('upload artifact'){
     steps {
       sh ' mvn deploy '

    }

    } //artifact upload to nexus repo stage completes here


    stage ('deploy  artifact'){
     steps {
       sh ' scp /root/workspace/whatsapp/chatting/build/sample-dev/target/studentapp-2.1.1-FEAT01-SNAPSHOT.war root@172.31.90.82:/opt/apache-tomcat-10.0.23/webapps '

    }

   } //install artifact on tomcat stage completes here



  }      //all stages complete here
   
}       // pipeline completes here
