pipeline {
    agent any
    stages {
        stage('Fetch') {
            steps {
                git branch: 'master', url:'https://github.com/chienphamvu/studentAttendance'
           }
        }
        stage('Build') {
            steps {
                sh 'javac net/codejava/Student.java'
            }
        }
        stage('Test') {
            steps {
                sh 'wget https://repo1.maven.org/maven2/junit/junit/4.13/junit-4.13.jar'
                sh 'wget https://repo1.maven.org/maven2/org/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.jar'

                sh 'javac -cp .:junit-4.13.jar:hamcrest-core-1.3.jar net/codejava/studentTest.java'
                sh 'java -cp .:junit-4.13.jar:hamcrest-core-1.3.jar org.junit.runner.JUnitCore net.codejava.studentTest'
            }
        }
    }
    post {
        always {
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'SUCCESS'
        }
        unstable {
            echo 'UNSTABLE'
        }
        failure {
            echo 'FAILED'
        }
    }
}
