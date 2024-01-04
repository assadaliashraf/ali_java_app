@Library('jenkins_shared_lib')_


pipeline{

    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
        string(name: 'ImageName', description: 'name of the Docker Build', defaultValue: 'javapp')
        string(name: 'ImageaTag', description: 'Tag of the Docker Build', defaultValue: 'v1')
        string(name: 'DockerHubUser', description: 'name of the Application', defaultValue: 'astivirgo')
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


        // stage('Unit Test Maven'){
        // when { expression {  params.action == 'create' } }
        //     steps{
        //         script{
        //             mvnTest()

                   
        //         }


        //     }
        // }
        // stage('Maven Integration Test'){
        // when { expression {  params.action == 'create' } }
        //     steps{
        //         script{
        //             mvnintegrationtest()

                   
        //         }


        //     }
        // }

        // stage('Static Code Analysis: Sonarqube'){
        // when { expression {  params.action == 'create' } }
        //     steps{
        //         script{
        //             def sonarqubecredentialsId = 'sonar-api'
        //             staticCodeAnalysis(sonarqubecredentialsId)

                   
        //         }


        //     }
        // }
        
        // stage('Quality Gate status check : Sonarqube'){
        // when { expression {  params.action == 'create' } }
        //     steps{
        //         script{
        //             def sonarqubecredentialsId = 'sonar-api'
        //             staticCodeAnalysis(sonarqubecredentialsId)

                   
        //         }


        //     }
        // }

        stage('Maven Build'){
        when { expression {  params.action == 'create' } }
            steps{
                script{
                    mvnBuild()

                   
                }


            }
        }

        stage('Docker Image Build'){
        when { expression {  params.action == 'create' } }
            steps{
                script{
                    dockerBuild("${params.ImageName}", "${params.ImageaTag}","${params.DockerHubUser}")

                   
                }


            }
        }

        stage('Docker Image Scan : Trivy'){
        when { expression {  params.action == 'create' } }
            steps{
                script{
                    dockerImageScan("${params.ImageName}", "${params.ImageaTag}","${params.DockerHubUser}")

                   
                }


            }
        }

        stage('Docker Image Push  : DockerHub'){
        when { expression {  params.action == 'create' } }
            steps{
                script{
                    dockerImagePush("${params.ImageName}", "${params.ImageaTag}","${params.DockerHubUser}")

                   
                }


            }
        }








    }



}