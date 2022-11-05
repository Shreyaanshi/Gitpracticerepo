pipeline {
    agent any
        triggers {
                CRON('* 18 * * 1-5')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: "qa", url: 'https://github.com/Shreyaanshi/Gitpracticerepo.git'
            }
                }
                 
                 stage ('Artifactory configuration') {
            steps {
                
                rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                    serverId: "JFROG_OCT22",
                    releaseRepo: 'qt-libs-release-local',
                    snapshotRepo: 'qt-libs-snapshot-local'
                )
                            }
        }
        stage ('Exec Maven') {
            steps {
                rtMavenRun (
                    tool: 'MVN_DEFAULT', 
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: "MAVEN_DEPLOYER"
                )
            }
        }

        }
}