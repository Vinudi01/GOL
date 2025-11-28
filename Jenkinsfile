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
        // copy war file
        sh 'cp /home/maxim/.gameoflife-build/gameoflife-web/target/gameoflife.war /opt/tomcat/webapps/'
      }
    }
  }
}

