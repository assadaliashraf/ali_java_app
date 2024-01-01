@Library('jenkins_shared_lib')_


pipeline{

    agent any

    stages{


        stage('Git Checkout'){

            steps{
                script{

                    gitCheckout(
                        branch: "master",
                        url: "https://github.com/assadaliashraf/ali_java_app.git"

                    )
                }


            }
        }


        stage('Unit Test Maven'){

            steps{
                script{
                    mvnTest()

                   
                }


            }
        }


    }



}