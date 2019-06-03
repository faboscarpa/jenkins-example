pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    echo env.BRANCH_NAME
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                when {
                expression {env.BRANCH_NAME == 'stagin'}
                }
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}