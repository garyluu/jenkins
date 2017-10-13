pipeline {
  agent any
  stages {
    stage('get') {
      steps {
        deleteDir()
        sh 'pip list'
        sh '''
dockstore tool launch --config /home/ubuntu/synapse/config --entry quay.io/ga4gh-dream/dockstore-tool-synapse-get:1.6.3 --json /home/ubuntu/synapse/hello_world_get.cwl.json'''
      }
    }
    stage('run') {
      steps {
        sh 'dockstore workflow launch --local-entry hello_world.cwl --json hello_world.cwl.json'
      }
    }
    stage('check') {
      steps {
        sh 'dockstore tool launch --local-entry hello_world_checker.cwl --json hello_world_checker.cwl.json'
      }
    }
    stage('grep') {
      steps {
        sh 'cat results.json | grep overall'
      }
    }
  }
}