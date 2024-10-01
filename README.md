<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>io.github.Jawad-Youness</groupId>
    <artifactId>MyFirstPublishedPackage</artifactId>
    <version>1.0.0</version>
    <name>My First Maven Central Package</name>
    <description>This was my first Maven Central published package.</description>
    <url>https://some.webpage.com</url>
    <properties>
        <maven.compiler.source>22</maven.compiler.source>
        <maven.compiler.target>22</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>
    <licenses>
        <license>
            <name>The Apache Software License, Version 2.0</name>
            <url>http://www.apache.org/licenses/LICENSE-2.0.txt</url>
            <distribution>repo</distribution>
        </license>
    </licenses>
    <developers>
        <developer>
            <id>Jawad-Youness</id> <!-- GitHub ID -->
            <name>Jawad Youness</name> <!-- Your name -->
            <email>fakeemail@fakedomain.com</email> <!-- Email -->
        </developer>
    </developers>
    <scm>
        <url>http://www.github.com/fakerepo</url> <!-- Changed back to OG SCM URL -->
    </scm>
    <build>
        <plugins>
            <!--  Define the plugin to sign the files using GPG  -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-gpg-plugin</artifactId>
                <version>3.2.2</version>
                <executions>
                    <execution>
                        <id>sign-artifacts</id>
                        <phase>verify</phase>
                        <goals>
                            <goal>sign</goal>
                        </goals>
                    </execution>
                </executions>
                <configuration>
                    <keyname>DB0464445122F53BD8803A182BC2822EDC2B0779</keyname> <!-- Updated Key ID -->
                    <gpgArguments>
                        <argument>--pinentry-mode</argument>
                        <argument>loopback</argument>
                    </gpgArguments>
                </configuration>
            </plugin>
            
            <!--  Define the plugin to attach the sources to the JAR file.  -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-source-plugin</artifactId>
                <version>3.3.1</version>
                <executions>
                    <execution>
                        <id>attach-sources</id>
                        <goals>
                            <goal>jar</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
            
            <!--  Define the plugin to attach the Javadocs to the JAR file.  -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-javadoc-plugin</artifactId>
                <version>3.6.3</version>
                <executions>
                    <execution>
                        <id>attach-javadocs</id>
                        <goals>
                            <goal>jar</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
            
            <!--  Define the plugin to deploy the artifacts to Maven Central.  -->
            <plugin>
                <groupId>org.sonatype.central</groupId>
                <artifactId>central-publishing-maven-plugin</artifactId>
                <version>0.4.0</version>
                <extensions>true</extensions>
                <configuration>
                    <autoPublish>true</autoPublish>
                    <deploymentName>MyInitialPackage</deploymentName>
                    <publishingServerId>central</publishingServerId>
                    <tokenAuth>true</tokenAuth>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
