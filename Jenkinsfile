// vi: ft=groovy
stage('Build') {
  node('linux') {
    echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
    checkout scm
    stash includes: '*', name: 'app'
  }
}
stage('Test') {
    node('linux') {
        checkout scm
        try {
            unstash 'app'
            sh 'ls -l'
        }
        finally {
          echo 'Finished tests in linux'
        }
    }
    node('windows') {
        checkout scm
        try {
            unstash 'app'
            echo "In windows"
            sh 'ls -l'
        }
        finally {
          echo 'Finished tests in windows'
        }
    }
}
