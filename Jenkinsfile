#!groovy

node("master"){
	stage 'clean, checkout and package install'
	sh "rm -rf *"
	checkout scm

	stage "Build"
	sh "ls -lh"
	dir("00-Starter-Seed"){
		sh "ls -lh"
		sh 'bower install'
		sh 'ls -la'
		stash 'webapp'
	}

}

stage "Deploy to DEV Bucket"
	node("master"){
		dir("staging"){
			unstash 'webapp'
			sh "aws s3 sync . s3://dhsflash-auth"
		}
	}
