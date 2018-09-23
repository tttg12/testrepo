node {
    // Change `url` value to your own
    //git url: 'file:////Users/evildethow/workspace/spike/project-w-property-files.git'
    
    def inputParams = inputParamsString()
    
    // Change `message` value to the message you want to display
    // Change `description` value to the description you want
    def selectedProperty = input( id: 'userInput', message: 'Choose properties file', parameters: [ [$class: 'ChoiceParameterDefinition', choices: inputParams, description: 'Properties', name: 'prop'] ])
    
    println "Property: $selectedProperty"
    
    // Change `job` value to your downstream job name
    // Change `name` value to the name you gave the string parameter in your downstream job
    //build job: 'downstream-freestyle', parameters: [[$class: 'StringParameterValue', name: 'prop', value: selectedProperty]]
}

import static groovy.io.FileType.FILES

@NonCPS
def inputParamsString() {
  def xml = "https://repository.jboss.org/nexus/service/local/lucene/search?g=jboss&a=jboss-j2ee&r=releases&p=jar".toURL().text

  def root = new XmlParser().parseText(xml)

  return root.data.artifact.collect {
    "${it.groupId.text()}:${it.artifactId.text()}:${it.version.text()}"
  }
}
