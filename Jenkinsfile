node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'docker -v'
      sh 'printenv'
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master'){
        sh 'docker build -t 10.168.2.134/di/react-app --no-cache .'
        sh 'docker push 10.168.2.134/di/react-app'
        sh 'docker rmi -f react-app 10.168.2.134/di/react-app'
      }
    }
  }
  catch (err) {
    throw err
  }
}
