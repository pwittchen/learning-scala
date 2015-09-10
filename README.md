# learning-scala
Repository created in order to learn basics of Scala language

IDE
---

IntelliJ IDEA with Scala plugin

Setting up Scala on Linux
-------------------------

- install Java
- install IntelliJ IDEA
- install Scala plugin for IntelliJ IDEA from Plugin repository
- download scala from http://www.scala-lang.org/download/
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
