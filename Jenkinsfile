pipeline {

  agent {
    label "Linux_Slave"
  }

  stages {
    
    stage('build') {
      steps {
        sh 'mvn clean install'
      }
    }

    stage('deploy') {
      steps {
        // stop tomcat
        sh 'sudo systemctl stop tomcat'

        // copy war file
        sh 'sudo cp /home/maxim/.gameoflife-build/gameoflife-web/target/gameoflife.war /opt/tomcat/webapps/'

        // start tomcat
        sh 'sudo systemctl start tomcat'
      }
    }
  }
}
