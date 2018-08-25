pipeline {
    agent { label "master"}
    stages {
        stage('1') {
            steps {
                script {
                    def tests = [:]
                    for (f in findFiles(glob: '/tmp/files/8.txt')) {
                        tests["${f}"] = {
                            node {
                                stage("${f}") {
                                    echo '${f}'
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
