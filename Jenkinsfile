pipeline {
    agent any

    stages {
        stage('Run JMeter Test') {
            steps {
                dir('CICDSCRIPTS') {
                    bat 'jmeter -n -t Maple.jmx -l results.jtl -e -o results'
                }
            }
        }

        stage('Archive Results') {
            steps {
                archiveArtifacts artifacts: '**/results.jtl', fingerprint: true
            }
        }
    }

    post {
        always {
            emailext (
                subject: "Jenkins CI - Build #${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
                body: """\
                    <p>Build Result: ${currentBuild.currentResult}</p>
                    <p>Check <a href="${env.BUILD_URL}">Jenkins Console Output</a></p>
                """,
                mimeType: 'text/html',
                to: "lbnaidu1995@gmail.com"
            )
        }
    }
}
