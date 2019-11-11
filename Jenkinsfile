properties([
  pipelineTriggers([pollSCM('H/3 * * * *')])
  ])
node() {
  cleanWs()
  checkout scm
  sh "make"
  sh "./main"
}
node {
  stage('build') {
    sh 'make'
  }
  stage('co') {
    checkout scm
  }
  stage('archi') {
    archiveArtifacts artifacts: 'main', onlyIfSuccessful: true
  }
}
