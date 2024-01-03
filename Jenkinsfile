@Library('jenkins_shared_lib')_


pipeline{

    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }

    stages{
        
        
        stage('Git Checkout'){
        when { expression {  params.action == 'create' } }
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
        when { expression {  params.action == 'create' } }
            steps{
                script{
                    mvnTest()

                   
                }


            }
        }
        stage('Maven Integration Test'){
        when { expression {  params.action == 'create' } }
            steps{
                script{
                    mvnintegrationtest()

                   
                }


            }
        }

        stage('Static Code Analysis: Sonarqube'){
        when { expression {  params.action == 'create' } }
            steps{
                script{
                    def sonarqubecredentialsId = 'sonar-api'
                    staticCodeAnalysis(sonarqubecredentialsId)

                   
                }


            }
        }
        
        stage('Quality Gate status check : Sonarqube'){
        when { expression {  params.action == 'create' } }
            steps{
                script{
                    def sonarqubecredentialsId = 'sonar-api'
                    staticCodeAnalysis(sonarqubecredentialsId)

                   
                }


            }
        }

    }



}