pipeline {
  agent { label "Linux_Slave" }

  stages {
    stage('build') {
      steps {
        sh 'mvn clean install -f /home/maxim/.gameoflife-build/gameoflife-web/pom.xml'
      }
    }

    stage('deploy') {
      steps {
        sh 'cp /home/maxim/.gameoflife-build/gameoflife-web/target/gameoflife.war /opt/tomcat/webapps/'
      }
    }
  }
}


