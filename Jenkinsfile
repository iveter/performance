pipeline {
    agent any

    stages {
        stage("Checkout") {
            steps {
                git branch: 'main', url: 'https://github.com/iveter/performance.git'
            }
        }

        stage('Test') {
            steps {
                sh "jmeter -Jjmeter.save.saveservice.output_format=xml -n -t cats.jmx -l cats.jtl"
            }
        }
        
        stage('Report'){
            steps{
                perfReport filterRegex: '', showTrendGraphs: true, sourceDataFiles: '**/*.jtl'
            }
        }
    }
}
