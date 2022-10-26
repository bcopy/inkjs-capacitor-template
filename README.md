# Inkjs Capacitor starter project with Maven

Why even ? Maven and the excellent [frontend plugin](https://github.com/eirslett/frontend-maven-plugin) provide a virtual environment for NPM-based development : 
* :relieved: Experiment safely with Node and NPM without messing with your operating system.
* :muscle: Let Maven handle the heavy-lifting related to Git flow releasing and versioning.

## How to boostrap your own Maven and NPM project

You need to register a Maven POM file using the Frontend plugin, as described on the [plugin homepage](https://github.com/eirslett/frontend-maven-plugin). Your configuration should specify the Node and NPM installation, here for instance with Node v12.x and NPM v6.x :

```xml
    <plugin>
        <groupId>com.github.eirslett</groupId>
        <artifactId>frontend-maven-plugin</artifactId>
        <version>1.12.1</version>
        <configuration>
            <workingDirectory>${project.basedir}</workingDirectory>
            <nodeVersion>v12.18.3</nodeVersion>
            <npmVersion>6.14.8</npmVersion>
        </configuration>
        <executions>
            <execution>
                <id>install node and npm</id>
                <goals>
                    <goal>install-node-and-npm</goal>
                </goals>
            </execution>
            <execution>
                <id>npm install</id>
                <goals>
                    <goal>npm</goal>
                </goals>
            </execution>
            <execution>
                <id>npm run build</id>
                <goals>
                    <goal>npm</goal>
                </goals>
                <configuration>
                    <arguments>run build</arguments>
                </configuration>
            </execution>
        </executions>
    </plugin>

```

Create a source folder, install NPM, extend your PATH then use ``npm init`` to create your ``package.json`` :

```bash
mvn com.github.eirslett:frontend-maven-plugin:install-node-and-npm
export PATH=`pwd`/node:`pwd`/bin:$PATH
npm init
```

You can then install the Capacitor toolset with :

```bash
npm i @capacitor/core
npm i -D @capacitor/cli
```


Happy coding 🎉🙌
