pipeline {
    agent any

    parameters {
        string(name: 'USERS', defaultValue: '1')
        string(name: 'LOOPS', defaultValue: '1')
    }

    stages {
        stage("Checkout") {
            steps {
                git branch: 'main', url: 'https://github.com/iveter/performance.git'
            }
        }

        stage('Test') {
            steps {
                sh "jmeter -Jjmeter.save.saveservice.output_format=xml -Jthreads=${USERS}  -Jloops=${LOOPS} -n -t cats.jmx -l cats.jtl"
            }
        }

        stage('Report') {
            steps {
                perfReport filterRegex: '', showTrendGraphs: true, sourceDataFiles: '**/*.jtl'
            }
        }
    }
}
