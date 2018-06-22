
import java.sql.DriverManager

DriverManager.registerDriver(new com.mysql.jdbc.Driver())

//Drop table if it already exists
//sql.execute('drop TABLE users')

node {
    
 
    currentBuild.result = 'SUCCESS'

    try {

        def ciEnv = "code1"

        stage('Prepare') {

       // \\slackSend message: "${env.JOB_NAME} - #${env.BUILD_NUMBER} Started... (<${env.BUILD_URL}|Open>)"

        checkout([
            $class: 'GitSCM',
            branches: [[name: '*/master']],
            doGenerateSubmoduleConfigurations: false,
            extensions: [],
            submoduleCfg: [],
            userRemoteConfigs: [[
                url: 'https://github.com/tomerb3/pipeline1.git'
            ]]
        ])

        stage("git-checkout") {

            if ("${REV_VER}" != 'master') {

                sh "git checkout ${REV_VER}"

            }
        }

    //    sh '${JENKINS_HOME}/workspace/it-build-tools/src/scripts/it-build-ctl init --ecr-login'

        }

        stage('run script a1') {

            sh '${JENKINS_HOME}/workspace/pipe1/scr1.sh ${REV_VER}'

        }

        stage('mysql 1') {

            //We can also insert by prepared statements by
          
                 def sql = Sql.newInstance("jdbc:mysql://192.168.14.91/world", "nativeuser", "password", "com.mysql.jdbc.Driver") 
         query = "SELECT * from country" 
         println sql.rows(query) 
         sql.close() 
            //sh '${JENKINS_HOME}/workspace/it-build-tools/src/scripts/it-build-ctl publish-rpms'
        //    sh 'env | sort'

         //   build job: 'seeded.rpm-publish', parameters: [string(name: 'SOURCE_WORKSPACE', value: "${env.WORKSPACE}"), string(name: 'TARGET_REPO', value: '')]

        }

        stage('Build-Containers') {

         //   sh '${JENKINS_HOME}/workspace/it-build-tools/src/scripts/it-build-ctl build-containers'

        }

        stage('Publish-Containers') {

        //    sh '${JENKINS_HOME}/workspace/it-build-tools/src/scripts/it-build-ctl publish-containers'

        }

        stage('Gather-Results') {
     //       archive 'target/**.rpm'
        }

        stage('Cleanup'){
            echo 'prune and cleanup'
         //   sh 'docker system prune --force'
            //sh 'rm -rf dist/builds'
        }

        stage((ciEnv ? ("Diagnose on " + ciEnv) : "Skip Diagnostics")) {

            if (ciEnv) {

             //   build job: "seeded.env." + ciEnv + ".diagnostics"

            } else {

            //    sh 'echo "WARNING: CI Environment Not Defined - Skipping..."'

            }

        }

    } catch (err) {

        currentBuild.result = "FAILURE"

        throw err

    } finally {

       // slackSend message: "${env.JOB_NAME} - #${env.BUILD_NUMBER} ${currentBuild.result} after ${currentBuild.durationString.replace(' and counting', '')} (<${env.BUILD_URL}|Open>)",
         //   color: ((currentBuild.result == "FAILURE")?"danger":"good")

    }

}

