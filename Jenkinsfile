// vi: ft=groovy
node { // <1>
    stage('Build') {
      checkout scm
      sh 'ls -l'
    }
    stage('Test') {
      // Will fail
      foobar
    }
    stage('Deploy') {
      echo "I am deploying"
    }
}
