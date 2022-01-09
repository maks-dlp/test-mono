pipeline {
  agent any
  stages {
    stage('Build Frontend') {
      agent { 
        docker { 
          image 'node:17.1.0-bullseye'
          reuseNode true
        }
      }
      when {
        changeset "**/packages/client/*.*"
        beforeAgent true
      }
      steps {
        dir('packages/client') {
          sh '''
            npm --version
            node --version
          '''
        }
      }
    }
  }
}
