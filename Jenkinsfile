#!groovy

@GrabConfig(systemClassLoader=true)
@Grapes([
    @Grab('mysql:mysql-connector-java:5.1.6')
])
import jenkins.*
import jenkins.model.*
import hudson.*
import hudson.model.*
import hudson.EnvVars
<<<<<<< HEAD
import groovy.sql.Sql

=======
 
import groovy.json.JsonSlurperClassic
import groovy.json.JsonBuilder
import groovy.json.JsonOutput
//import com.microsoft.sqlserver.jdbc.SQLServerDriver
>>>>>>> 8acd3f17ca182bcd238b0a7d47951645b3be3189

//@Library('DSG_PIPELINE') _
 

 

//import java.sql.DriverManager
//import jenkins.model.*
//jenkins = Jenkins.instance

//DriverManager.registerDriver(new com.mysql.jdbc.Driver())



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

        stage('sql 1') {

def project = env.JOB_NAME.split('/')[0]
println "${env.JOB_NAME}"
println project


//  def sql = Sql.newInstance("jdbc:sqlserver://oit-tomerb;DatabaseName=temp1", "tmp1","1234567", "com.mysql.jdbc.Driver")
//List a = sql.rows('SELECT name1 from projectinfo where id=1')
//def tomer = a[0][0]
//println tomer

      def sql = sql.newInstance("jdbc:mysql://192.168.14.91:3306/mysql", "tomer", "qwer90","com.mysql.jdbc.Driver")

          ansiColor('xterm') {
        // Just some echoes to show the ANSI color.
        stage "\u001B[31mI'm Red\u001B[0m Now not"

            }
            sql.close()

        echo "\u001b[34m Test Test"
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

