properties([pipelineTriggers([githubPush()])])

node('24aa0f436fb5') {   
  stage('Unit Tests') {    
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'
  }
  stage('Build') {
   sh 'ant  -f build.xml -v'
  }
}

