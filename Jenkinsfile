pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        echo 'Taking source checkout'
      }
    }
    stage('Build') {
      steps {
        echo 'Preparing Build'
	sh 'docker run --rm -p 8090:80 -v /home/andrew/src:/usr/share/nginx/html:ro -d nginx'
      }
    }
    stage('Test_Build') {
      steps {
        echo 'Test the site'
	sh 'curl localhost:8090 | grep -i "hello world" && echo "PipeLine has Run Successfully!"'
	sh 'sleep 2'
      }
    }
  }
}
