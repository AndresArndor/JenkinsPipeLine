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
	sh 'docker run --rm -v /home/vagrant/src:/var/www/html firespring/apache2-php'
      }
    }
    stage('Test_Build') {
      steps {
        echo 'Test the site'
	curl localhost
      }
    }
  }
}
