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
}
