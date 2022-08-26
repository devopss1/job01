node {
			stage('checkout from GitHub'){
						echo "Checkout the code from GITHUB"
						git 'https://github.com/devopss1/job01.git'
						}
			stage('Build with maven'){
						echo "Build / compile the code"
						sh 'mvn package -f pom.xml'
						}
			stage('Artifactory upload to Nexus'){
						echo "upload to nexus artifactory repository"
						nexusArtifactUploader artifacts: [[artifactId: 'google', classifier: '', file: '/var/lib/jenkins/workspace/job01/target/google-1.0-SNAPSHOT.jar', type: 'jar']], credentialsId: 'nexus', groupId: 'brillius.devops', nexusUrl: '192.168.0.11:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '1.0-SNAPSHOT'
						}
			stage('Deploy to web-server'){
						echo "Deploy the jar/war to web server"
	                    sh 'cp  /var/lib/jenkins/workspace/job01/target/google-1.0-SNAPSHOT.jar /tmp/apache-tomcat-9.0.65/webapps/'					
						}
			stage('post action'){
						echo " send notification after deploy"
						}

            }
