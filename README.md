# learning-scala
Repository created in order to learn basics of Scala language

Notes about Scala
-----------------

Notes from Scala tutorial are available in [`NOTES.md`](https://github.com/pwittchen/learning-scala/blob/master/NOTES.md) file

IDE
---

IntelliJ IDEA with Scala plugin

Setting up Scala on Linux
-------------------------

- install Java
- install IntelliJ IDEA
- install Scala plugin for IntelliJ IDEA from Plugin repository
- download Scala from http://www.scala-lang.org/download/
  - `wget http://downloads.typesafe.com/scala/2.11.7/scala-2.11.7.tgz`
- extract downloaded archive
  - `tar -xzvf scala-2.11.7.tgz`
- rename extracted directory to `scala` and copy it to `/usr/share/` directory
  - `sudo cp -avr scala /usr/share` 
  - [copy command explanation*](http://www.cyberciti.biz/faq/copy-folder-linux-command-line/)
- add appropriate environmental variables to your `.bashrc` or `.zshrc` file
```
export SCALA_HOME=/usr/local/share/scala
export PATH=$PATH:$SCALA_HOME/bin
```

**OR** skip all the steps above and just use [SDKMan](https://sdkman.io/).

Compiling and running programs
------------------------------

- Create Scala project
- Put path to JDK. In my case: `/usr/lib/jvm/java-8-oracle`
- Put path to Scala SDK: `/usr/local/share/scala`
- Create file `HelloWorld.scala`

```scala
object HelloWorld {
  def main(args: Array[String]) {
    println("Hello, world!")
  }
}

```

- Right click on on `main(...)` function and choose `Run`.

SBT
---

SBT is the interactive build tool for Scala. Use Scala to define your tasks. Then run them in parallel from the shell.

Visit [official website](http://www.scala-sbt.org/) and check instructions for [installing SBT on Linux](http://www.scala-sbt.org/0.13/tutorial/Installing-sbt-on-Linux.html), which are as follows:

```
echo "deb https://dl.bintray.com/sbt/debian /" | sudo tee -a /etc/apt/sources.list.d/sbt.list
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 642AC823
sudo apt-get update
sudo apt-get install sbt
```

References
----------
- [Official Scala website](http://www.scala-lang.org)
- [Official Scala documentation](http://www.scala-lang.org/documentation/)
- [Getting started](http://www.scala-lang.org/documentation/getting-started.html)
- [Scala Tutorial for Java Programmers](https://www.scala-lang.org/docu/files/ScalaTutorial.pdf)
- [Scala tutorial](https://www.tutorialspoint.com/scala/index.htm)
- [Scala video tutorial (1h)](https://www.youtube.com/watch?v=DzFt0YkZo8M)
- [Scala video tutorial - cheatsheet](http://www.newthinktank.com/2015/08/learn-scala-one-video/)
- [Scala for the impatient - book](http://www.amazon.com/Scala-Impatient-Cay-S-Horstmann/dp/0321774094/)
- [Scala SBT](http://www.scala-sbt.org/)
- [Scala SBT downloads](http://www.scala-sbt.org/download.html)
- [Installing SBT on Linux](http://www.scala-sbt.org/0.13/tutorial/Installing-sbt-on-Linux.html)
