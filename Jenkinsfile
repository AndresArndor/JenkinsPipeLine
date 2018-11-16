pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        svn 'http://49.249.225.174:8585/repos/RABITSRC/RABIT/branches/CustomUtils-Dev'
        tool(name: 'Maven 3.5', type: 'maven')
      }
    }
    stage('Build') {
      steps {
        sh '''if (isUnix()) {
         sh "\'${mvnHome}/bin/mvn\' clean package -DskipTests=true -Dsonar.host.url=http://sonar.autorabit.com/ -Dsonar.login=sreenivasrao.m -Dsonar.password=Sree4R@b1t jdepend:generate linkcheck:linkcheck checkstyle:checkstyle pmd:pmd pmd:cpd changelog:changelog changelog:dev-activity changelog:file-activity -Dscm.url=http://49.249.225.174:8585/repos/RABITSRC/RABIT/branches/CustomUtils-Dev -Dusername=sreenivasrao.m -Dpassword=sreenivasrao.m!"
      } else {
         bat \'${mvnHome}\\\\bin\\\\mvn clean package -DskipTests=true -Dsonar.host.url=http://sonar.autorabit.com/ -Dsonar.login=sreenivasrao.m -Dsonar.password=Sree4R@b1t jdepend:generate linkcheck:linkcheck checkstyle:checkstyle pmd:pmd pmd:cpd changelog:changelog changelog:dev-activity changelog:file-activity -Dscm.url=http://49.249.225.174:8585/repos/RABITSRC/RABIT/branches/CustomUtils-Dev -Dusername=sreenivasrao.m -Dpassword=sreenivasrao.m!\'
      }'''
        }
      }
    }
    environment {
      mvnHome = ''
    }
  }