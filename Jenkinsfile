pipeline {
    agent any

    stages {
        stage("Checkout") {
//             steps {
//                 git branch: 'main', url: 'git@github.com:iveter/perfomance.git'
//             }
        }

        stage('Test') {
            steps {
                sh "jmeter -Jjmeter.save.saveservice.output_format=xml -n -t cats.jmx -l cats.jtl"
            }
        }
    }
}
