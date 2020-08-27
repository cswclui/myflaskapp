pipeline {
  agent { docker { image 'python:3.8' } }
  stages {
    stage('build') {
      steps {
		   sh '''
				python -m venv .venv
				. .venv/bin/activate
				pip install -r requirements.txt
			
			'''
      
      }
    }
    stage('test') {
      steps {
		   sh '''
				source .venv/bin/activate
				pytest --junit-xml test-reports/results.xml code/flask_app_test.py
				
			'''
       
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
  }
}





