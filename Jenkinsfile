pipeline {
agent any
        tools{
        maven 'M2_HOME'
        jdk 'JAVA_HOME'
        }
        stages{
               stage('build'){
                              steps{
                              bat 'mvn compiler:compile'
                              }
                              post{
                   success{
                   bat "echo 'projet compile with success'"
                   }
                   failure{
                   bat "echo 'error when compiling the project'"
                   }
               }
                 }
                 stage('test'){
               steps{
                  bat 'mvn test'
                              }
                              post{
                   always{
                   junit 'target/surefire-reports/*.xml'
                   }
                   
                  }
               }
                       stage('couverture'){
               steps{
                  bat 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
                              }
                              post{
                                  always{
                                        cobertura coberturaReportFile: '**target/site/cobertura/coverage.xml'
                                      }
                   
                                   }
                               }
                }
       }
