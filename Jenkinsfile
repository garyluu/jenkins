pipeline {
  agent any
  stages {
    stage('get') {
      steps {
        deleteDir()
        sh 'pip list'
        sh 'dockstore -v'
        sh 'dockstore tool launch --config /home/ubuntu/synapse/config --entry quay.io/ga4gh-dream/dockstore-tool-synapse-get --json /home/ubuntu/synapse/biowardrobe_chipseq_se_get.cwl.json'
      }
    }
    stage('run') {
      steps {
        sh 'dockstore workflow launch --local-entry biowardrobe_chipseq_se.cwl --json biowardrobe_chipseq_se.json'
      }
    }
    stage('check') {
      steps {
        sh 'dockstore tool launch --local-entry biowardrobe_chipseq_se_checker.cwl --json biowardrobe_chipseq_se_checker.json'
      }
    }
    stage('grep') {
      steps {
        sh 'cat results.json | grep overall'
      }
    }
  }
}