pipeline {
  agent any
  stages {
    stage('Compile Stage') {
      agent {
        docker {
          image 'maven:3.3-jdk-8'
          args '-v /root/.m2:/root/.m2'
        }

      }
      steps {
        withMaven(maven: 'maven_3_5_0') {
          sh 'mvn clean compile'
        }

      }
    }
    stage('Testing Stage') {
      agent {
        docker {
          args '-v /root/.m2:/root/.m2'
          image 'maven:3.3-jdk-8'
        }

      }
      steps {
        withMaven(maven: 'maven_3_5_0') {
          sh 'mvn test'
        }

      }
    }
    stage('Deployment Stage') {
      agent {
        docker {
          args '-v /root/.m2:/root/.m2'
          image 'maven:3.3-jdk-8'
        }

      }
      steps {
        withMaven(maven: 'maven_3_5_0') {
          echo 'Deployando'
        }

      }
    }
  }
}