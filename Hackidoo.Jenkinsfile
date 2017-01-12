prodFilesToRemove = ['.gitignore', 'test.zip', 'test.txt', 'deleteMe.js']
devFilesToRemove = []

node {
    //currentBuild.result = "STARTED"
    stage('Cloning Project') {
        git 'https://github.com/tmrocha89/hackidoo'
    }
    //currentBuild.result = "TESTING"
    stage('Tests') {
        def tests = [:] //empty map
        tests["Unit test"] = {
            node{
                echo "Running tests A"
                sleep 3
                exit 0
            }
        }
        tests["Usability test"] = {
            node{
                echo "Running more tests :)"
                sleep 5
                exit 0
            }
        }

        tests.failFast = true   //if any one of the tests fail, the build fails
        parallel tests
        //sh 'echo "Nothing to test. TDD? nop!"'
    }
    milestone()
    stage('Add Random Files') {
        touch file: 'test.zip', timestamp: 0
        touch file: 'test.txt', timestamp: 0
        touch file: 'deleteMe.js', timestamp: 0
    }
    stage('Build a zip file') {
        buildZip(env.buildFor)
    }

    //currentBuild.result = "SUCCESS"

}



def buildZip (buildFor){
    def fileName = buildFor+"-hackidoo.zip"
    def list = buildFor == "DEV" ? devFilesToRemove : prodFilesToRemove 
    sh 'echo "removing files"'
    for(item in list){
        sh 'echo "removing '+item+'"'
    }

    zip archive: true, dir: '', glob: '', zipFile: fileName 

}