properties([pipelineTriggers([githubPush()])])

node('Assignment10') {   
  stage('Unit Tests') {    
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'
  }   
  stage('Build') {    
    sh 'ant'   
  }
}
