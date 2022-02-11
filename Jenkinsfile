node('master') {
//  ansiColor('xterm') {
	stage ('checkout code'){
		checkout scm
	}
	
	stage ('Build'){
		sh "mvn clean install -Dmaven.test.skip=true"
		echo "Buiding Stage done!"
	}

	stage ('Test Cases Execution'){
		sh "mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install -Pcoverage-per-test"
		echo "Test Cases mack Execution Stage done!"
	}

	stage ('Sonar Analysis'){
		//sh 'mvn sonar:sonar -Dsonar.host.url=http://35.153.67.119:9000 -Dsonar.login=77467cfd2653653ad3b35463fbfdb09285f08be5'
		echo "Run Sonar Qube Execution Stage done!"
	}

	stage ('Archive Artifacts'){
		archiveArtifacts artifacts: 'target/*.war'
	}
	
	stage ('Deployment'){
		//deploy adapters: [tomcat9(credentialsId: 'TomcatCreds', path: '', url: 'http://52.90.29.200:8080/')], contextPath: null, war: 'target/*.war'
		echo "Deployment using ansible will be added!"
	}
	stage ('Notification'){
		//slackSend color: 'good', message: 'Deployment Sucessful'
		emailext (
		      subject: "Job Completed test",
		      body: "Jenkins Pipeline Job for Maven Build got completed !!!",
		      to: "hassan.mcsd@hotmail.com"
		    )
	}
  // }
}
