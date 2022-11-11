pipeline{
    agent{
        agent any
        tools {
            docker 'docker'
        }
    
    stages{
        stage("docker installation"){
            steps{
                sh "yum install docker -y"
                sh "docker --version"
            }
            post{
                
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        
        stage("docker container"){
            step{
                sh "docker run -it -p 8732:8732 --name python:3.10-buster /bin/bash"
    }
            post{
                
                success{
                    echo "====++++docker container executed successfully++++===="
        }
                failure{
                    echo "====++++docker container execution failed++++===="
        }
        
            }
        }
        stage("clone"){
            steps{
                git "https://github.com/varunlamp/semaphore-demo-python-django.git"
            }
            post{
                
                success{
                    echo "====++++clone executed successfully++++===="
                }
                failure{
                    echo "====++++clone execution failed++++===="
                }
        
            }
        }
        stage("docker DB"){

            steps{
                sh pip install requirement.txt
            }
            post{
                   
                    success{
                        echo "====++++manage executed successfully++++===="
                    }
                    failure{
                        echo "====++++manage execution failed++++===="
                    }
            
                }
        }
            stage("manage"){
                steps{
                    sh "python manage.py migrate"
                }
                post{
                   
                    success{
                        echo "====++++manage executed successfully++++===="
                    }
                    failure{
                        echo "====++++manage execution failed++++===="
                    }
            
                }
            }
            stage("build"){
                steps{
                    sh "python run -it -p 0.0.0.0:8732"
                }
                post{
                    
                    success{
                        echo "====++++build executed successfully++++===="
                    }
                    failure{
                        echo "====++++build execution failed++++===="
                    }
            
                }
            }
           
        
    }

}