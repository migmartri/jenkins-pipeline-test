// vi: ft=groovy
node { // <1>
    stage('Build') {
      echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
      checkout scm
      sh 'ls -l'
    }
    stage('Test') {
      echo 'Test!'
    }
    stage('Deploy') {
      echo "I am deploying"
    }
}
