1.  `git clone` this project
2. Download GraalVM for JDK 21 Community 21.0.2 : https://github.com/graalvm/graalvm-ce-builds/releases/download/jdk-21.0.2/graalvm-community-jdk-21.0.2_linux-x64_bin.tar.gz
3. Add it to your PATH and export JAVA_HOME

```bash
export JAVA_HOME=/path/to/graalvm/untared
export PATH=$JAVA_HOME/bin:$PATH
```

4. `cd /path/to/cloned/repo`
5. `./mvnw clean -Pnative native:compile` or `./mvnw -e -X clean -Pnative native:compile` for more logging
6. Wait a few minutes
7. segfault
