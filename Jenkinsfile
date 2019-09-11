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
	sh 'docker run --rm --name some-nginxi -p 8090:80 -v /home/vagrant/src:/usr/share/nginx/html:ro -d nginx'
      }
    }
    stage('Test_Build') {
      steps {
        echo 'Test the site'
	sh 'curl localhost:8090 | grep -i "hello world" && echo "PipeLine has Run Successfully!"'
	sh 'sleep 3'
	sh 'docker stop some-nginxi'
      }
    }
  }
}
