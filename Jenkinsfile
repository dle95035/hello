@Library('Utilities@master')  
import static org.conf.Utilities.* 
node('worker_node3'){
		// get source.
		stage('Source') { 
			git 'https://github.com/dle95035/hello.git' 
		}
		
		// get source.
		stage('Build') { 
			gbuild this, 'clean build' 
		}
		
		// use local shared libary.
		stage ('Verify') { 
			def verifyCall = load("/root/repos/library/src/verify.groovy") 
			
			// get user input with timeout of 5 seconds.
			timeout(time: 5, unit: 'SECONDS') {
				verifyCall("Please Verify the build") 
			}
		} 
}
