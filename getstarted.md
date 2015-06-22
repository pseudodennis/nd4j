---
layout: page
title: "Get started with ND4J in Minutes"
description: "Follow our video and install a Java development environment ready for N-Dimensional Array Algebra with ND4J"
---
{% include JB/setup %}

To get started with ND4J and DL4J, review and setup the following:

1. [Prerequisites](#prereq) 
3. [Integrated Development Environment](#ide-for-java) 
4. [Github](#github)
5. [Next Steps](#next-steps)

## <a id="prereq"> Prerequisites </a>

System configuation requirements:

* [Java 7](#java) 
* [Scala 2.10.4](#scala)
* [Maven 3.2.5](#maven)
* [Canova 0.0.0.2](#canova)

Distributed systems using Spark requirements: 

* [Spark 1.3.0](https://spark.apache.org/downloads.html) _(package type = Pre-built for Hadoop 1.X)_

GPU(s) requirements:

* [Cuda 7](http://docs.nvidia.com/cuda/index.html#axzz3dlfIdQjP)

## <a id="java">Java</a>

Java is the main programming language of ND4J. There are about 9 million Java developers worldwide. It runs on 3 billion mobile phones and 97 percent of all enterprise desktops, both Windows and OSX. Java is used for everything from distributed cloud-based systems with thousands of nodes, to low-memory IoT devices. It's a "write once, run anywhere" language.

### Installing Java

To test which version of Java you have (and whether you have it at all), type the following into your command line:

		java -version

ND4J and DL4J require **Java 7**, so if you have an older or newer version, you will need to reinstall.

If you don't have Java 7 installed on your machine, download the [Java Development Kit (JDK) here](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html). The download will vary by operating system. For newer Macs, you'll want the file on the first line to mention Mac OS X (the number after *jdk-7u* increments with each update). It will look something like this:

		Mac OS X x64 185.94 MB -  jdk-7u79-macosx-x75.dmg

## <a id="scala">Scala</a>

Scala is an object-oriented langauge like Java with a strong static type system and it runs on teh JVM. The difference is that it has functional programming features similar to Scheme and Haskell and its structure keeps programs consice. You can use Java libraries with Scala. We provide a [Scala API](http://nd4j.org/scala.html). There are neural net examples you can run written in Scala, and it is requried for Spark implementation.

### Installing Scala

To test which version of Java you have (and whether you have it at all), type the following into your command line:

		scala -version

In order to install Scala, checkout this [link](http://www.scala-lang.org/download/2.10.4.html).

## <a id="maven">Maven</a>

Maven is an automated build tool for Java projects (among other [things](http://maven.apache.org/what-is-maven.html)), which locates the latest version of the project libraries (ND4J .jar files) and downloads them automatically to your computer. We've written a slightly more thorough [introduction to Maven for non-Java programmers](http://deeplearning4j.org/maven.html) here. Maven will allow you to install both ND4J and Deeplearning4j projects easily. It works well with Integrated Development Environments ([IDE](#ide)) such as IntelliJ.

*(Experienced Java developers who prefer not to work with Maven can find the .jar files on our [downloads](downloads.html) page. For an expert user, the downloads may be faster, but for beginners, they are also more complicated to use, due to dependencies.)*

### Installing Maven

To see if Maven is installed in your machine, enter the following into the command line:

		mvn --version

Instructions to install Maven are [here](https://maven.apache.org/download.cgi). Download the compressed file containing Maven's latest stable version. 

![Alt text](../img/maven_downloads.png) 

Lower on the same Web page, follow the instructions that pertain to your operating system; e.g. *"Unix-based Operating Systems (Linux, Solaris and Mac OS X)."* They look like this:

![Alt text](../img/maven_OS_instructions.png) 

## <a id="ide">Integrated Development Environments</a>

An Integrated Development Environment ([IDE](http://encyclopedia.thefreedictionary.com/integrated+development+environment)) will allow you to work with our API and build your nets with a few clicks. We suggest **IntelliJ**. It will work with your installed version of Java and can communicate with [Maven](#maven), which takes care of the dependencies for you. 

An IDE provides a hassle-free development environment that allows you to focus more on your code. IDEs typically come with Maven support, but we prefer you to install [Maven](#maven) so you can run commands directly. While we prefer IntelliJ, [Eclipse](http://books.sonatype.com/m2eclipse-book/reference/creating-sect-importing-projects.html) and [Netbeans](http://wiki.netbeans.org/MavenBestPractices) are two other popular IDEs.

### Installing an IDE

The free community edition of [IntelliJ](https://www.jetbrains.com/idea/download/) has installation instructions.

## Starting a New ND4J Project

Now, using your IDE, create a new project. Select `maven-archetype-quickstart`. 

![Alt text](../img/new_maven_project.png) 

The images below will walk you through the windows of the IntelliJ New Project Wizard using Maven. First, name your group and artifact. If you're building a deeplearning4j project, you'll want org.deeplearning4j in the GroupID slot; if the project is simply for ND4J, you'll want org.nd4j, and so on. The artifact can be any name you choose.

![Alt text](../img/maven2.png) 

Click through the following screen with "Next", and on the screen after that, name your project ("ND4J-test", for example) and hit finish. Now go into your pom.xml file within the root of the new ND4J project in IntelliJ. 

Update the POM file with needed dependences. For example, include the default backend ([Jblas](http://en.wikipedia.org/wiki/Jblas:_Linear_Algebra_for_Java)) in the `<dependencies> ... </dependencies>` section, so that Maven can automatically install the required libraries:

	 <dependency>
	   <groupId>org.nd4j</groupId>
	   <artifactId>nd4j-jblas</artifactId>
	   <version>${nd4j.version}</version>
	 </dependency>
	 
ND4J's version is a variable here. It will refer to another line higher in the POM, in the <properties> ... </properties> section, specifying the nd4j version and appearing similar to this:

		<nd4j.version>0.0.3.5.5.3</nd4j.version>

The number of the version will vary with new releases. Make sure you check the latest version available on Maven. 

Keep in mind that the JBLAS backend can be switched to Netlib Blas, or to Jcublas for GPU use. Check our [dependencies](../dependencies.html) page for advanced configuration changes. That page also explains how to check on the [latest version](http://search.maven.org/#search%7Cga%7C1%7Cnd4j) of the libraries.

Open App.java file that is created with every new Intellij project, and start writing code between the curly brackets you see after **public static void main( String[] args )**. 

Many of the classes will appear in red, since you haven't imported the right packages, but IntelliJ will add those packages automatically to the top of your file. Lookup the appropriate hot keys based on your OS to help automatically load the packages. 

You can now create a new Java file within IntelliJ, and start using ND4J's API for distributed linear algebra. (See our [intro](http://nd4j.org/introduction.html) for a couple beginning operations. ND4J in IntelliJ has **autocomplete**, so starting a new line with any letter will show you a list of all ND4J commands including that letter.) 

## <a id="canova">Canova</a>

[Canova](https://github.com/deeplearning4j/Canova) is a general vectorization lib we built for machine-learning tools. It vectorizes raw data into usable vector formats like svmLight, libsvm and ARFF, which our neural nets can work with.

### Installing Canova

Take the same steps to install [Canova](http://search.maven.org/#search%7Cga%7C1%7Ccanova-parent) using Maven that you followed for ND4J. 

### Installing Deeplearning4j

Deeplearning4j versions should be specified in the same way you did for ND4J, which the version in properties and the variable in the dependencies. 

The DL4J dependencies you add to the POM will vary with the nature of your project. In addition to the core dependency, given below, you may also want to install deeplearning4j-cli for the command-line interface, deeplearning4j-scaleout for running parallel on Hadoop or Spark, and others as needed... A full list will come up by searching for *deeplearning4j* on Maven Central.

		   <dependency>
		     <groupId>org.deeplearning4j</groupId>
		     <artifactId>deeplearning4j-core</artifactId>
		     <version>${deeplearning4j.version}</version>
		   </dependency>

More information on installing Deeplearning4j is available on its [Getting Started page](http://deeplearning4j.org/gettingstarted.html).

## <a id="github">GitHub (Optional)</a>

[Github](http://en.wikipedia.org/wiki/GitHub) is a web-based [Revision Control System](http://en.wikipedia.org/wiki/Revision_control), _the [de facto host](http://opensource.com/life/12/11/code-hosting-comparison) for open source projects_.

**You are not required to install GitHub**. If you're planning to contribute to the ND4J or [DeepLearning4J](https://github.com/SkymindIO/deeplearning4j) projects by fixing bugs and committing code, you will need git and GitHub. (Thanks in advance btw :)

### Installing Git &/or GitHub (Optional)

Type the following into your command line to verify you have git.

		git --version 

Just check the list of applications installed on your computer for GitHub.

To use GitHub, first install [git](https://git-scm.herokuapp.com/book/en/v2/Getting-Started-Installing-Git) if you do not have it already. Then setup a [Github account](https://github.com/join). Download GitHub for [Mac](https://mac.github.com/), [Windows](https://windows.github.com/), etc. Once installed, clone ND4J or DL4J, enter this command into your terminal (Mac) or Git Shell (Windows):

      git clone https://github.com/SkymindIO/nd4j
      git clone https://github.com/SkymindIO/deeplearning4j
      
You might also want to clone our examples so you can mess around with ND4J or DL4J's pre-built samples:
      
      git clone https://github.com/SkymindIO/nd4j-examples
      git clone https://github.com/SkymindIO/dl4j-examples
      
Another way to get the source code is by clicking on the "[download ZIP](https://github.com/SkymindIO/nd4j/archive/master.zip)" button from the [ND4J GitHub page](https://github.com/SkymindIO/nd4j). Then unzip the file (you can use [7-zip](http://www.7-zip.org/download.html) to do that).

Maven can be used in conjunction with Git to ensure that ND4J, Canova and Deeplearning4j build correctly. To make sure you have the most recent, working version of these libraries, you can *cd* into their root directories and enter the following command into your prompt:

		mvn clean install -DskipTests -Dmaven.javadoc.skip=true

Running a clean install on ND4J, Canova and Deeplearning4j, in that order, is a good way to get the most recent bug fixes and features. 

## <a id="next-steps">Next Steps</a>

Now you're ready to run the [examples](introduction.html). We recommend that you launch your IDE, load the ND4J project and open the examples subdirectory. Locate an example in the file tree on the lefthand side of the IntelliJ window, right click on it, and select the green arrow for "Run" on the drop-down menu. 

If everything was installed correctly, you should see numbers appear as the program output at the bottom of the IntelliJ window. Please use these as a sandbox to start experimenting.  

Once you're comfortable with the examples, you might want to change the dependencies defined in the POM files. Learn how to change the [dependencies here](gpu_native_backends.html).

For questions or feedback, join us on our [Google Groups Forum](https://groups.google.com/forum/#!forum/nd4j).

## Useful links

* [ND4J Github repository](https://github.com/deeplearning4j/nd4j)
* [ND4J Maven Repository](http://mvnrepository.com/artifact/org.nd4j)
* [DeepLearning4j.org](http://deeplearning4j.org/)
* [DeepLearning4j Github repository](https://github.com/deeplearning4j/deeplearning4j)
* [DeepLearning4j Maven Repository](http://mvnrepository.com/artifact/org.deeplearning4j)