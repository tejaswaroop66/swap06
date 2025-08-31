pipeline {
  agent { label 'agent' }
  tools { maven 'maven3'; jdk 'java17' }

  stages {
    stage('Checkout'){ steps { git url: 'https://github.com/tejaswaroop66/swap06.git', branch: 'master' } }
    stage('Build')   { steps { sh 'mvn -DskipTests clean package' } }
    stage('Deploy')  { steps { sh '''
      sudo rm -rf /var/lib/tomcat10/webapps/ROOT /var/lib/tomcat10/webapps/ROOT.war
      sudo cp target/swap06.war /var/lib/tomcat10/webapps/ROOT.war
      sudo systemctl restart tomcat10
    ''' } }
  }
}
