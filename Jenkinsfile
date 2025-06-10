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
                    bat 'C:\\Users\\LekkalaBhupal\\Desktop\\Performance-Testing-Tools\\apache-jmeter-5.5\\apache-jmeter-5.5\\bin\\jmeter.bat -n -t Maple.jmx -l results.jtl -e -o results'
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
