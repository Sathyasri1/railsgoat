pipeline{
  agent any
  stages{
    stage('Bomanai'){
      steps{
         sh 'pip install --extra-index-url https://test.pypi.org/simple/ boman-cli-uat==14.0.2'
         sh 'id -u -n'
         sh '~/.local/bin/boman-cli-uat -a run -u https://qa.boman.ai'
      }
    }
  }
}
