pipeline {
  agent any
  stages {
    stage('get') {
      steps {
        sh 'dockstore tool launch --config /home/ubuntu/synapse/config --entry quay.io/ga4gh-dream/dockstore-tool-synapse-get --json /home/ubuntu/synapse/md5sum_get.cwl.json'
      }
    }
    stage('run') {
      steps {
        sh 'dockstore workflow launch --local-entry md5sum.cwl --json md5sum.cwl.json'
      }
    }
    stage('check') {
      steps {
        sh 'dockstore tool launch --local-entry md5sum_checker.cwl --json md5sum_checker.cwl.json'
      }
    }
    stage('grep') {
      steps {
        sh 'cat results.json | grep Overall'
      }
    }
  }
}