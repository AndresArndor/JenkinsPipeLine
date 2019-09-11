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
	sh 'docker run --rm --name some-nginxi -p 8080:80 -v /home/vagrant/src:/usr/share/nginx/html:ro -d nginx'
      }
    }
    stage('Test_Build') {
      steps {
        echo 'Test the site'
	sh 'curl localhost:8080 | grep -ri "hello world" && echo "PipeLine has Run Successfully!"'
	sh 'sleep 3'
	sh 'docker stop some-nginxi'
      }
    }
  }
}
