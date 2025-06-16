@Library('jenkins-shared-libaries')_

def configMap = [
    project : "expense",
    component : "backend"
]



if ( ! env.BRANCH_NAME.equalsIgnoreCase('main')) {
    nodeJSEKSPipeline(configMap)
}
else {
    echo " please follow production process"
}