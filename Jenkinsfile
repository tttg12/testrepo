pipeline {
    agent any
    // Change `url` value to your own
    //git url: 'file:////Users/evildethow/workspace/spike/project-w-property-files.git'
    stages {    
        stage('inp') {
            steps {
                script {
                    def inputParams = inputParamsString().tokenize(',')

                    // Change `message` value to the message you want to display
                    // Change `description` value to the description you want
                    def selectedProperty = input( id: 'userInput', message: 'Choose properties file', parameters: [ [$class: 'ChoiceParameterDefinition', choices: inputParams, description: 'Properties', name: 'prop'] ])

                    println "Property: $selectedProperty"

                    // Change `job` value to your downstream job name
                    // Change `name` value to the name you gave the string parameter in your downstream job
                    //build job: 'downstream-freestyle', parameters: [[$class: 'StringParameterValue', name: 'prop', value: selectedProperty]]
                }
            }
        }
    }
}

@NonCPS
def inputParamsString() {
  def xml = "https://repository.jboss.org/nexus/service/local/lucene/search?g=jboss&a=jboss-j2ee&r=releases&p=jar".toURL().text

  //def root = new XmlParser().parseText(xml)
  def response = new XmlSlurper().parseText(xml)
  def versions = response.data.artifact.collect{ it.version }.join(",")
  //versions = ["1.1.1","2.2.2"]
  print("versions=${versions}")
  return versions
    //root.data.artifact.collect {
   // "${it.groupId.text()}:${it.artifactId.text()}:${it.version.text()}"
  //}
}


