// vi: ft=groovy
stage('Build') {
  node {
    echo "Running ${env.BUILD_ID} on branch ${env.BRANCH_NAME}"
    checkout scm
    stash includes: '*', name: 'app'
  }
}
stage('Test') {
    parallel branch_1: {
      node {
          checkout scm
          try {
              unstash 'app'
              sh 'ls -l'
              sh 'sleep 10'
          }
          finally {
            echo 'Finished tests in linux'
          }
      }
    },
    branch_2: {
      node {
          checkout scm
          try {
              unstash 'app'
              echo "In windows"
              sh 'ls -l'
              sh 'sleep 8'
          }
          finally {
            echo 'Finished tests in windows'
          }
      }
    }
}
