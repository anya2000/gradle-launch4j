# Introduction #

The gradle-launch4j plugin uses [launch4j](http://launch4j.sourceforge.net/) to create windows .exe files for java applications. Launch4j must be installed as well to use this plugin.


# Tasks #

There are 4 tasks:
  * generateXmlConfig - Creates XML configuration file used by launch4j.
  * copyL4jLib - Copies the project dependency jars in the lib directory.
  * createExe - Runs launch4j to generate an .exe file.
  * launch4j - Placeholder task that depends on the above.

Launch4j must be installed separately as it includes native code.

# Configuration #

The configuration follows the structure of the launch4j xml file. See the launch4j documentation for the meanings. The gradle-launch4j plugin tries to pick sensible defaults based on the project. The only required
value is the mainClassName.

An example configuration within your build.gradle might look like:
```
apply plugin: 'launch4j'

launch4j {
    mainClassName = "com.example.myapp.Start"
    icon = 'icons/myApp.ico'
}


buildscript {
    repositories {
        mavenCentral()
    }

    dependencies {
        classpath 'edu.sc.seis.gradle:launch4j:1.0.6'
    }
}
```

See the [Gradle User guide](http://gradle.org/docs/current/userguide/custom_plugins.html#customPluginStandalone) for more information on how to use a custom plugin.

The values configurable within the launch4j extension along with their defaults are:

  * String launch4jCmd = "launch4j"
  * String outputDir = "launch4j"
  * String xmlFileName = "launch4j.xml"
  * String mainClassName
  * boolean dontWrapJar = false
  * String headerType = "gui"
  * String jar = "lib/"+project.tasks[JavaPlugin.JAR\_TASK\_NAME].outputs.files.getSingleFile().name
  * String outfile = project.name+'.exe'
  * String errTitle = ""
  * boolean cmdLine = false
  * String chdir = '.'
  * String priority = 'normal'
  * String downloadUrl = ""
  * String supportUrl = ""
  * boolean customProcName = false
  * boolean stayAlive = false
  * String manifest = ""
  * String icon = ""
  * String version = project.version
  * String copyright = "unknown"
  * String opt = ""
  * String bundledJrePath
  * String jreMinVersion = project.targetCompatibility
  * String jreMaxVersion
  * String mutexName
  * String windowTitle
  * String messagesStartupError
  * String messagesBundledJreError
  * String messagesJreVersionError
  * String messagesLauncherError
  * Integer initialHeapSize
  * Integer initialHeapPercent
  * Integer maxHeapSize
  * Integer maxHeapPercent