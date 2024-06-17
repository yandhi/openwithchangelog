def fetchLatestVersion() {
    def changelogContent = readFile 'CHANGELOG.md'

    // Updated regex pattern to match new heading format
    def matcher = (changelogContent =~ /## \[(\d+\.\d+\.\d+)\]/)
    if (matcher) {
        return matcher[0][1]
    } else {
        error "Failed to find a version in the CHANGELOG.md"
    }
}

pipeline {
    agent any

    stages {
        stage('Fetch Latest Version') {
            steps {
                script {
                    def latestVersion = fetchLatestVersion()
                    echo "Latest Version: ${latestVersion}"
                }
            }
        }
    }
}