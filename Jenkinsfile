pipeline {
    agent any

    stages {
        stage('Install Playwright Browsers') {
            steps {
                bat "npx playwright install" // Install the required browsers
            }
        }

        stage('Building') {
            steps {
                echo "Building the project"
            }
        }

        stage('Testing') {
            steps {
                bat "npm ci"
                bat "npm run TestScenarios" // Command to run all scenarios
            }
        }

        // stage('Generate Report') {
        //     steps {
        //         sleep time: 15, unit: 'SECONDS'
        //         bat "npx ts-node generateReport.ts" // Command to generate reports
        //     }
        // }

        stage('Deploying') {
            steps {
                echo "Deploying project"
            }
        }

        stage('Publish Report') {
            steps {
                publishHTML([
                    allowMissing: false, 
                    alwaysLinkToLastBuild: true, 
                    keepAll: false, 
                    reportDir: "cypress", // Update this to your report directory if different
                    reportFiles: "index.html", 
                    reportName: 'HTML Report', 
                    reportTitles: ''
                ])
            }
        }
    }
}
