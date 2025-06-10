pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run JMeter Test') {
            steps {
                // Navigate to workspace/CICDSCRIPTS and run JMeter
                dir('CICDSCRIPTS') {
                    bat 'jmeter -n -t Maple.jmx -l results.jtl -e -o results'
                }
            }
        }

        stage('Archive Results') {
            steps {
                archiveArtifacts artifacts: 'CICDSCRIPTS/results/**/*.*', fingerprint: true
            }
        }
    }
}
