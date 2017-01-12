prodFilesToRemove = ['.gitignore', 'test.zip', 'test.txt', 'deleteMe.js']
devFilesToRemove = []

node {
    stage('Cloning Project') {
        git 'https://github.com/tmrocha89/hackidoo'
    }
    stage('Unit Tests') {
        def tests = [:] //empty map
        tests[0] = {
            node{
                echo "Running tests A"
                sleep 10
            }
        }
        tests[1] = {
            node{
                echo "Running more tests :)"
                sleep 5
            }
        }

        tests.failFast = true
        parallel tests
        //sh 'echo "Nothing to test. TDD? nop!"'
    }
    stage('Add Random Files') {
        touch file: 'test.zip', timestamp: 0
        touch file: 'test.txt', timestamp: 0
        touch file: 'deleteMe.js', timestamp: 0
    }
    stage('Build a zip file') {
        buildZip(env.buildFor)
    }


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