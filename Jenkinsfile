#!/usr/bin/env groovy
def appName = 'scheduleDynamoDBToSnowFlake';
def appVersion = '1.0.0';
// Run during a maintenance window for the master branch
// Once every 8:00 a.m. TODO: scheduling would be once a day

String cronExpression = "H 9 * * *";
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
      tools{
          nodejs "node"
      }
          stages{
              stage("Build"){
                  steps{
                      sh 'echo "Hello Schedule"'
                  }
              }
            stage("Test"){
                steps{
                    sh '''
                    pwd
                    ls
                    cd constants
                    ls
                    node --version
                    node schedules.js
                    '''
                }
            }
            
          }

      }

