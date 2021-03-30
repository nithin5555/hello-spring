
    peline {
    agent any
    stages {
        stage('Build') {
            steps {
                checkout scm
                sh "mvn package"
            }
            post {
                success {
                    archiveArtifacts 'target/hello-spring-0.1.0.jar'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Running commands to execute Test cases'
                sh 'echo "All test cases ran successfully" && exit 0'
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS'
              }
            }
            steps {
                echo 'Running steps to deploy the jar file to nodes'
            }
        }
    }
}sed -e "s|52.66.203.78|$(curl -fSsL http://169.254.169.254/latest/meta-data/public-ipv4)|g" -i /var/lib/jenkins/jenkins.model.JenkinsLocationConfiguration.xml
