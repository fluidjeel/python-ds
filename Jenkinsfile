pipeline {
	agent {
		label 'master'
	}
	tools {
		maven 'M3'
		git 'git'
	}
	stages {
		stage ('Git Pull'){
			steps {
				echo "Pull sources from GH"
			}
		}
		stage ('Is this required'){
			steps {
				echo " Check for holiday"
			}

		}
		stage ('Build') {
			steps {
				echo "Build the sources"
			}
		}
		stage ('Quality Check and UnitTest') {
			parallel {
				stage ('Quality Check'){
					stages {
						stage ('Static_Check') {
							steps {
								echo "Run SC sources"
							}
						}
						stage ('QA') {
							steps {
								echo "Run QA"
							}
						}

					}
				}
				stage ('Unit_Test') {
					steps {
						echo "Run UT"
					}
				}
			}
		}
		stage ('Summary') {
			steps {
				echo "summary"
			}
		}



	}
	post {
		always {
			echo "Build Completed"
		}
		success {
			echo "Build Completed successfully"
		}
		failure {
			echo "Build has errors, refer to console"
		}
	}

}
