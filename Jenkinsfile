pipeline {
  agent any
  tools {
    maven 'maven-3.9'
  }
  stages {
    stage("build jar") {
      steps {
        script {
          echo "building the application..."
        }
        sh 'mvn package'
      }
    }

    stage("build image") {
      steps {
        script {
          echo "building the docker image..."
          withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
            sh "docker build -t azeshion21/demo-app:jma-2.8 ."
            sh "echo $PASS | docker login -u $USER --password-stdin"
            sh 'docker push azeshion21/demo-app:jma-2.8'
          }
        }
      }
    }

    stage("deploy") {
      steps {
        script {
          echo "deploying the application..."
          // Add deployment steps here
        }
      }
    }
  }
}
