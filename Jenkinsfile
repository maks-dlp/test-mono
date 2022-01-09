pipeline {
  agent any
  stages {
    stage('Build Frontend') {
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
