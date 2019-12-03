#!/usr/bin/env groovy
def appName = 'scheduleDynamoDBToSnowFlake';
def appVersion = '1.0.0';
String cronExpression = "* * * * *"
  properties([
    parameters([
      booleanParam(
        defaultValue: true,
        description: 'Click this checkbox to run data validation',
        name: 'RUN_DATA_VALIDATION'
      ),
    ]),
    pipelineTriggers([
      cron(cronExpression)
    ]),
    disableConcurrentBuilds()
  ])
  pipeline{
      agent any
      {
          stages{
              stage("Build"){
                  steps{
                      sh 'echo "Hello Schedule"'
                  }
              }
              stage("Test"){
                  steps{
                      sh ' echo "New World"'
                  }
              }
          }
      }
  }
// Run during a maintenance window for the master branch
// Once every 8:00 a.m. TODO: scheduling would be once a day

// if (env.BRANCH_NAME == 'master') {

// }


// node('worker') {
//   def pipeline;

//   pipeline = new cicd.Pipeline();

//   stage('Prepare Pipeline') {
//     pipeline.cleanupAndCheckout();
//   }

//   stage('Gradle build') {
//     docker.image('maven:3.3.9-jdk-8').inside() {
//       sh './gradlew clean build'
//     }
//   }

//   stage('Run Validator') {
//     if (env.RUN_DATA_VALIDATION == 'true') {
//       withCredentials([
//         usernamePassword(
//           credentialsId: 'SVC_SNOWFLAKE_PROD',
//           usernameVariable: 'SPRING_DATASOURCE_USERNAME',
//           passwordVariable: 'SPRING_DATASOURCE_PASSWORD',
//         ),
//       ]) {
//         withEnv(['DEPLOY_ENV='+env.DEPLOY_ENV]) {
//           docker.image('maven:3.3.9-jdk-8').inside() {
//             sh 'java -jar build/libs/com.athenahealth.validation.data-validation-0.1.0.jar'
//           }
//         }
//       }
//     }
//   }

//   stage('Final Cleanup') {
//     deleteDir();
//   }

//   stage('Notify') {
//     slackSend(
//       channel: '#qmii',
//       color: 'good',
//       message: "Data Validation - CLDP diff QMaaS\n" +
//         "See the report at (<${currentBuild.absoluteUrl}|Open>)",
//       tokenCredentialId: "SlackToken"
//     )
//   }

// }