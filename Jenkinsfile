pipeline {
  agent {
    label 'linux'
  }
  stages {
    stage('Build Frontend') {
      agent { 
        docker { 
          image 'node:17.1.0-bullseye'
          reuseNode true
        }
      }
      when {
        changeset "**/frontend/*.*"
        beforeAgent true
      }
      steps {
        dir('frontend') {
          sh '''
            npm --version
            node --version
            cat frontend.txt
          '''
        }
      }
    }
    stage('Build Web') {
      agent { 
        docker { 
          image 'maven:3.8.3-openjdk-17'
          reuseNode true
        }
      }
      when {
        changeset "**/backend/web/*.*"
        beforeAgent true
      }
      steps {
        dir ('backend/web') {
          sh 'mvn --version'
          sh 'cat web.txt'
        }
      }
    }
    stage('Build REST API') {
      agent { 
        docker { 
          image 'golang:1.17.3-bullseye'
          reuseNode true
        }
      }
      when {
        changeset "**/backend/api/*.*"
        beforeAgent true
      }
      steps {
        dir ('backend/api') {
          sh 'go version'
          sh 'cat api.txt'
        }
      }
    }
  }
}
