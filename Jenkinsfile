// vi: ft=groovy
stage('Build') {
  node('linux') {
    echo "Running ${env.BUILD_ID} on branch ${env.BRANCH_NAME}"
    checkout scm
    stash includes: '*', name: 'app'
  }
}
stage('Test') {
    parallel linux: {
      node('linux') {
          checkout scm
          try {
              unstash 'app'
              sh 'ls -l'
              sh 'sleep 7'
          }
          finally {
            echo 'Finished tests in linux'
          }
      }
    },
    windows: {
      node('windows') {
          checkout scm
          try {
              unstash 'app'
              echo "In windows"
              sh 'ls -l'
              sh 'sleep 5'
          }
          finally {
            echo 'Finished tests in windows'
          }
      }
    }
}
