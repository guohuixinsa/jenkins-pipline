pipeline {
  agent {
    node {
      label '10.80.105.188'
    }

  }
  stages {
    stage('Download') {
      parallel {
        stage('Download') {
          steps {
            echo '"Download repo"'
          }
        }
        stage('BuildNotest') {
          steps {
            libraryResource 'harmanBuild'
          }
        }
      }
    }
  }
}