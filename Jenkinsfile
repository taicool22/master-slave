pipeline{
    agent 
    stages{
        stage('1-repoClone'){
            steps{
                sh 'pwd'
            }
        }
        stage('2-parallel job'){
            agent {
                label 'slave1'
            }
            parallel{
                stage('1-identification'){
                    steps{
                        sh 'whoami'
                    }
                }
                stage('2-subjob'){
                    agent{
                        label 'slave2'
                    }
                }
                    steps{
                        sh 'echo "my name is taiwo"'
                    }
                }
                stage('3-subjob3'){
                    steps{
                        sh 'touch taiwo.txt'
                    }
                }
                stage('4-subjob4'){
                    agent {
                        label 'slave3'
                    }
                    steps{
                        sh 'echo "my name?" > taiwo.txt'
                    }
                }
            }
        }
        stage('2-cpuAnalysis'){
            steps{
                sh 'lscpu'
            }
        }
        stage('3-memoryCheck'){
            steps{
                sh 'free -g'
            }
        } 
        stage('4-os-stats'){
            agent {
                label 'slave1'
            }
            steps{
                sh 'cat /etc/os-release'
            }
        }   
    
    }
}
