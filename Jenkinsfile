pipeline {
  agent any
  stages {
    stage('get') {
      steps {
        deleteDir()
        sh 'pip list'
        sh 'dockstore tool launch --config /home/ubuntu/synapse/config --entry quay.io/ga4gh-dream/dockstore-tool-synapse-get --json /home/ubuntu/synapse/bcbio_NA12878-chr20_get.cwl.json'
      }
    }
    stage('run') {
      steps {
        sh 'dockstore workflow launch --local-entry NA12878-platinum-chr20-workflow/main-NA12878-platinum-chr20.cwl --json NA12878-platinum-chr20-workflow/main-NA12878-platinum-chr20-samples.json --script'
      }
    }
    stage('check') {
      steps {
        sh 'dockstore tool launch --local-entry bcbio_NA12878-chr20_checker.cwl --json bcbio_NA12878-chr20_checker.json'
      }
    }
    stage('grep') {
      steps {
        sh 'cat results.json | grep overall'
      }
    }
  }
}