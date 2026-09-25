---
layout: post
title: Installing Apache Spark on macOS
subtitle: A practical setup guide
cover-img: /assets/img/chair_lift.jpg
thumbnail-img: /assets/img/chair_lift.jpg
share-img: /assets/img/chair_lift.jpg
tags: [tech, python, spark] 
---

I recently bought the reference book "Spark: The Definitive Guide" by Bill Chambers and Matei Zaharia, to try to become more proficient in Spark, and found it surprisingly challenging to get clear instructions on how to configure Spark on a macOS. After trying and failing to get Spark set up a number of different ways, I finally found a set of install steps that were simple to execute and successful.

NOTE: This set up uses Homebrew, so if you don't already have that, install it first:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

1. Install OpenJDK via Homebrew
Spark needs Java installed because it runs on the Java Virtual Machine (JVM).
```
brew install openjdk@17
```

2. Export `PATH` and `JAVA_HOME` to your `.zshrc` or `.bashrc`
```
echo 'export JAVA_HOME=$(/usr/libexec/java_home -v 17)' >> ~/.zshrc
echo 'export PATH="$JAVA_HOME/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

3. Verify the Java version points to the one installed above
```
java --version
```

4. Verify the Spark installation
```
spark-submit --version
```

5. Verify `pyspark` starts an interactive shell
```
pyspark
```

Once these steps have been completed and validated, you should be all set to start write Spark jobs.