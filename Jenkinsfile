properties([pipelineTriggers([githubPush()])])

node('24aa0f436fb5') {   
  stage('Unit Tests') {
    git 'https://github.com/ludewiaj/java-project.git' 
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'
  }
  stage('Build') {
   sh 'ant  -f build.xml -v'
  }
  stage('Deploy') {
    sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-BUILD_NUMBER.jar s3://assignment-10-jar-bucket/rectangle-BUILD_NUMBER.jar'
  }
}

