#!groovy​

@Library('Utilities@master')  
import static org.conf.Utilities.* 
node('worker_node2'){

	try {
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
	catch (err) { 
		echo "Caught: ${err}"       
	} 
	stage('Parallel Test 1') {
		parallel linux: {
			echo "Linux Linux"
			sleep 7
			echo "done Linux sleep"
        },
		windows: {
			echo "Windows 10 11 12"
			sleep 4
        }
	}
	stage('Parallel Test 2') {
		def tests = [:]
        for (def option in ["Linux", "Windows"]) {
			if ("Linux" == "${option}") {
				tests["${option}"] = {
					echo "Linux Linux"
					sleep 7
					echo "done Linux sleep"
				} 
			} else {
				tests["${option}"] = {
					echo "Windows 10 11 12"
					sleep 4
				} 
			}
        }
		parallel tests
	}
	stage ('Notify') { 
		
		//mailUser(<email address in single quotes>,"Finished") 
		echo "==> finished."
	} 
}
