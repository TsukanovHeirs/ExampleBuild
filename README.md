# ExampleBuild

### Entry 

Перед тем, как выполнять пробовать повторить описанное ниже, нужно установить IDE для Java, Git (если не установлен). 
Среди IDE можно выбрать любую, конечно, но советую остановиться на Intellij IDEA, ибо она крайне удобная и приятная в использовании. Версия (Ultimate или Community) не имеет значения. Саму джаву мы устанавливать не будем (она сама встанет).
 


***ВАЖНО!*** При установке лучше поставить галочки у пунктов Update PATH Variable и Add "Open Folder as Project". Так же ставим галочки на Create Associations у .java, .gradle, .groovy. Шорткат уже на ваше усмотрение.
___

## Создание проекта

Перед работой в самой IDE нужно будет создать GitHub репозиторий. Теперь по пунктам:

* Создаем папку, через правую кнопку мыши делаем Git Bash. 
* С главной страницы вашего реаозитория копируем https (через раздел <>Code)
* Пишем в Bash команду git init "httpsstring" (вставлять без кавычек).

Теперь создание проекта. В начальном окне IDE будет предложена возможность создать проект. Кликаем, создаем в папке, куда копировали репозиторий. 
А теперь по пунткам:

* Соблюдайте нэйминг, он будет важен. Так же для удобства могу предложить не раскидывать все проекты по жесткому диску, а создать отдельную папку и уже там делать всё связанное.
* Среди языков выбираем Java, система сборки Gradle.
* ***ВАЖНО!*** В пункте JDK выбираем версию 16 и более. IDE предложит установить JDK этой версии, СОГЛАШАЕМСЯ.
* Ниже (в Gradle DSL) выбираем Groovy.

___

## Настройка проекта

В самой IDE зайдите в настройки: File -> Settings -> "Build, Execution, Deployment" -> "Build Tools" -> Gradle. Есть вероятность, что Gradle user home будет стоять по умолчанию. Если это так, стоит установить Gradle и поставить в этом поле папку .gradle. Этот пункт советую проделать только в том случае, если после прохождения всей инструкции возникли проблемы с сборкой проекта.

Нужно будет поправить файлы .gitignore и build.gradle. Хотел бы заметить, что build.gradle придется менять под каждый новый модуль.

И в завершении распаковать себе архив прямо в проект с некоторыми другими файлами.

.gitignore:
```
# Created by https://www.toptal.com/developers/gitignore/api/java,gradle,intellij+all
# Edit at https://www.toptal.com/developers/gitignore?templates=java,gradle,intellij+all

### Intellij+all ###
# Covers JetBrains IDEs: IntelliJ, RubyMine, PhpStorm, AppCode, PyCharm, CLion, Android Studio, WebStorm and Rider
# Reference: https://intellij-support.jetbrains.com/hc/en-us/articles/206544839

# User-specific stuff
.idea/**/workspace.xml
.idea/**/tasks.xml
.idea/**/usage.statistics.xml
.idea/**/dictionaries
.idea/**/shelf

# AWS User-specific
.idea/**/aws.xml

# Generated files
.idea/**/contentModel.xml

# Sensitive or high-churn files
.idea/**/dataSources/
.idea/**/dataSources.ids
.idea/**/dataSources.local.xml
.idea/**/sqlDataSources.xml
.idea/**/dynamic.xml
.idea/**/uiDesigner.xml
.idea/**/dbnavigator.xml

# Gradle
.idea/**/gradle.xml
.idea/**/libraries

# Gradle and Maven with auto-import
# When using Gradle or Maven with auto-import, you should exclude module files,
# since they will be recreated, and may cause churn.  Uncomment if using
# auto-import.
# .idea/artifacts
# .idea/compiler.xml
# .idea/jarRepositories.xml
# .idea/modules.xml
# .idea/*.iml
# .idea/modules
# *.iml
# *.ipr

# CMake
cmake-build-*/

# Mongo Explorer plugin
.idea/**/mongoSettings.xml

# File-based project format
*.iws

# IntelliJ
out/

# mpeltonen/sbt-idea plugin
.idea_modules/

# JIRA plugin
atlassian-ide-plugin.xml

# Cursive Clojure plugin
.idea/replstate.xml

# SonarLint plugin
.idea/sonarlint/

# Crashlytics plugin (for Android Studio and IntelliJ)
com_crashlytics_export_strings.xml
crashlytics.properties
crashlytics-build.properties
fabric.properties

# Editor-based Rest Client
.idea/httpRequests

# Android studio 3.1+ serialized cache file
.idea/caches/build_file_checksums.ser

### Intellij+all Patch ###
# Ignore everything but code style settings and run configurations
# that are supposed to be shared within teams.

.idea/*

!.idea/codeStyles
!.idea/runConfigurations

### Java ###
# Compiled class file
*.class

# Log file
*.log

# BlueJ files
*.ctxt

# Mobile Tools for Java (J2ME)
.mtj.tmp/

# Package Files #
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar

# virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xml
hs_err_pid*
replay_pid*

### Gradle ###
.gradle
**/build/
!src/**/build/

# Ignore Gradle GUI config
gradle-app.setting

# Avoid ignoring Gradle wrapper jar file (.jar files are usually ignored)
!gradle-wrapper.jar

# Avoid ignore Gradle wrappper properties
!gradle-wrapper.properties

# Cache of project
.gradletasknamecache

# Eclipse Gradle plugin generated files
# Eclipse Core
.project
# JDT-specific (Eclipse Java Development Tools)
.classpath

### Gradle Patch ###
# Java heap dump
*.hprof

# End of https://www.toptal.com/developers/gitignore/api/java,gradle,intellij+all
```

build.gradle:
```
plugins {
    id 'java'
    id 'jacoco'
}

group 'itmo.is.bushuev'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.8.1'
    testImplementation 'org.junit.jupiter:junit-jupiter-params:5.8.2'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.8.1'
}

test {
    useJUnitPlatform()
}
/*
jacoco {
    toolVersion = "0.8.8"
    reportsDirectory = layout.buildDirectory.dir('customJacocoReportDir')
    //Если включите данную опцию, то в воркфлоу у метки #JCC, поменяйте путь
}
 */
jacocoTestReport {
    dependsOn test // tests are required to run before generating the report
    reports {
        xml.required = true
        //html.outputLocation = layout.buildDirectory.dir('jacocoHtml') Доп опция, чтобы у себя можно было открыть html
    }
    afterEvaluate {
        classDirectories.setFrom(files(classDirectories.files.collect {
            fileTree(dir: it, exclude: [
                    "Main.class",
                    //"<package>.Main.class" Указывайте полное имея пакета с точками
            ])
        }))
    }

}

```

___

## Настройка IDE

Если есть желание как-то поменять внешний вид (тему), то в правом верхнем углу в разделе настроек выбираем нужный пункт.

![image](https://user-images.githubusercontent.com/131151302/234003507-052cb6a3-babd-4921-bf4f-a414296baa93.png)


___
