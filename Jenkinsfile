pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
		checkout scm
	    }
	}
	stage('Build') {
	    steps {
		sh '/home/ubuntu/apache-maven-3.6.1//bin/mvn install'
	}
	    }
	stage('Deployment') {
	    steps {
		sh 'sshpass -p "boni" scp target/gamutkart.war gamut@172.17.0.2:/home/gamut/Distros/apache-tomcat-8.5.42/webapps'
		sh 'sshpass -p "boni" ssh gamut@172.17.0.2 "JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64" "TOMECAT_HOME=/home/ubuntu/apache-tomcat-8.5.45//bin/startup.sh"'
	    }
	}

    }
}
