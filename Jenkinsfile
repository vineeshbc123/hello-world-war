pipeline {
  agent {label 'slave1'}
  stages {
    stage ('my build') {
      steps {
        sh 'mvn package'  
        sh 'pwd'
        sh 'ls'
      }
    }
    stage ('my deploy') {
    agent {label 'slave2'}
     steps {
        sh 'sudo cp -R target/hello-world-war-1.0.0.war /opt/apache-tomcat-10.0.27/webapps/'
        sh 'sudo sh /opt/apache-tomcat-10.0.27/bin/shutdown.sh'
        sh 'sleep 2'
        sh 'sudo sh /opt/apache-tomcat-10.0.27/bin/startup.sh'
      }
    }
  }
}
