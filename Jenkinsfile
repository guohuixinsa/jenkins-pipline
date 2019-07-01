@Library('harmanBuild') _
@NonCPS
def getDownloadType(Build,Params,ENV){
    println Build
    println Params
    def SCM = Build.project.getSCMs()
    println SCM
    println Build.project.getSCMs()[1].type
    androidEmail(Build,Params,ENV) 
    def dateS = new org.version.dateString()
}

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
            checkout([$class: 'RepoScm', cleanFirst: true, currentBranch: true, destinationDir: 'android', forceSync: true, ignoreProjects: 'gwm_v3mh/manifest', jobs: 8, manifestBranch: 'gwmv3-my20-mainline', manifestRepositoryUrl: 'ssh://androidhub.harman.com:29418/android/manifest', mirrorDir: '/mnt/mirror', noTags: true, repoBranch: 'harman-stable', repoUrl: 'ssh://androidhub.harman.com:29418/harman/repo', resetFirst: true])
          }
        }
        stage('BuildNotest') {
          steps {
             dir("${WORKSPACE}") {
                       getDownloadType(currentBuild.rawBuild,params,env)
                    }
          }
        }
      }
    }
  }
}
