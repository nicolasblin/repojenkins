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
  stage('checkout') {
    checkout scm
  }
  stage('archivage') {
    archiveArtifacts artifacts: 'main', onlyIfSuccessful: true
  }
}
