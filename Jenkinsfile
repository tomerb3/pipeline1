pipeline {
    agent { label "master"}
    stages {
        stage('1') {
            steps {
                script {
                    def tests = [:]
                    for (f in findFiles(glob: '**/*.sh')) {
                        tests["${f}"] = {
                            node {
                                stage("${f}") {
                                    echo '${f}'
                                    dir ('/var/lib/jenkins/workspace/pipe1') { 
                                      sh('script.sh kk1')
                                    }
                                 
                                }
                            }
                        }
                    }
                    parallel tests
                }
            }
        }       
    }
}
