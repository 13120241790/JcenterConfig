# JcenterConfig

# Step 1


root build.gradle add ：

` 
// Top-level build file where you can add configuration options common to all sub-projects/modules.

buildscript {
    repositories {
        jcenter()
        mavenCentral()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.1.2'
        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.7'
        classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5'

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}

allprojects {
    repositories {
        jcenter()
        mavenCentral()
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
 `
 
# Step 2

library build.gradle add：


`
apply plugin: 'com.android.library'

android {
    compileSdkVersion 23
    buildToolsVersion "23.0.3"

    defaultConfig {
        minSdkVersion 14
        targetSdkVersion 23
        versionCode 1
        versionName "1.0"
    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
}

ext {
    bintrayRepo = 'maven'
    bintrayName = 'netlibrary'

    publishedGroupId = 'com.netlibrary'
    artifact = 'network'

    siteUrl = 'https://github.com/13120241790/NetLibrary'
    gitUrl = 'https://github.com/13120241790/NetLibrary.git'

    libraryVersion = '1.0.1'
    libraryName = 'netlibrary'
    libraryDescription = 'AM Code for Android'

    developerId = 'zhouxuming'
    developerName = 'Zhou Xuming'
    developerEmail = '13120241790@163.com'


    licenseName = 'The Apache Software License, Version 2.0'
    licenseUrl = 'http://www.apache.org/licenses/LICENSE-2.0.txt'
    allLicenses = ["Apache-2.0"]
}
apply from:'https://raw.githubusercontent.com/13120241790/JcenterConfig/master/install.gradle'
apply from:'https://raw.githubusercontent.com/13120241790/JcenterConfig/master/bintray.gradle'

`

# Step 3

local.properties add:

`

sdk.dir=/Users/zhouxuming/Library/Android/sdk
bintray.apikey=221bea1b435d2702fc54211e9faa5f66e28501a8
bintray.user=13120241790

`

# Step 4

Terminal input: ./gradlew bintrayupload



#End



> apply from:'https://raw.githubusercontent.com/13120241790/JcenterConfig/master/install.gradle'
apply from:'https://raw.githubusercontent.com/13120241790/JcenterConfig/master/bintray.gradle'