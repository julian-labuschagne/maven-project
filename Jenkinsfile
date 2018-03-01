pipeline {
  agent any
  stages{
    stage('Init'){
      steps {
        echo "Testing..."
      }
    }

    stage('Build'){
      steps {
        sh '/usr/local/apache-maven-3.5.2/bin/mvn clean package'
      }
      post {
        success {
          echo 'Now Archiving...'
          archiveArtifacts artifacts: '**/target/*.war'
        }
      }
    }

    stage('Deploy to Staging'){
      steps {
        build job: 'deploy-to-staging'
      }
    }
  }
}
