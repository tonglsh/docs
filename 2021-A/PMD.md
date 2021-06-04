## PMD

https://pmd.github.io/

https://pmd.github.io/pmd-6.31.0/

![PMD - Don't shoot the messenger](https://pmd.github.io/img/pmd_logo.png)

### An extensible cross-language static code analyzer.



##### What does 'PMD' mean?

> We’ve been trying to find the meaning of the letters PMD - because frankly, we don’t really know. We just think the letters sound good together.
>
> However, in the spirit of the Computing Industry, we have come up with several “backronyms” to explain it.
>
> **PMD…**
>
> - Pretty Much Done
> - Project Mess Detector
> - Project Monitoring Directives
> - Project Meets Deadline
> - Programming Mistake Detector
> - Pounds Mistakes Dead
> - PMD Meaning Discovery (recursion, hooray!)
> - Programs of Mass Destruction
> - Programming Meticulous coDe
> - [A ‘Chaotic Metal’ rock band name](http://www.myspace.com/prettymarydies)



## QuickStart(cli)See also [Getting Started](https://pmd.github.io/pmd-6.31.0/pmd_userdocs_installation.html)

```bash
$ cd $HOME
$ wget https://github.com/pmd/pmd/releases/download/pmd_releases%2F6.31.0/pmd-bin-6.31.0.zip
$ unzip pmd-bin-6.31.0.zip
$ alias pmd="$HOME/pmd-bin-6.31.0/bin/run.sh pmd"
$ pmd -d /usr/src -R rulesets/java/quickstart.xml -f text
```

### pmd

```
./run.sh pmd d /home/tonglsh/IdeaProjects/demo-pmd/src -R rulesets/java/quickstart.xml -f json

```

```json
{                                                                                                                                             
  "formatVersion": 0,                                                                                                                         
  "pmdVersion": "6.31.0",                                                                                                                     
  "timestamp": "2021-02-07T13:43:25.277+08:00",                                                                                               
  "files": [                                                                                                                                  
    {                                                                                                                                         
      "filename": "/home/tonglsh/IdeaProjects/demo-pmd/src/main/java/Acc/dd.java",                                                            
      "violations": [                                                                                                                         
        {                                                                                                                                     
          "beginline": 1,                                                                                                                     
          "begincolumn": 9,                                                                                                                   
          "endline": 1,                                                                                                                       
          "endcolumn": 11,                                                                                                                    
          "description": "Package name contains upper case characters",                                                                       
          "rule": "PackageCase",                                                                                                              
          "ruleset": "Code Style",                                                                                                            
          "priority": 3,                                                                                                                      
          "externalInfoUrl": "https://pmd.github.io/pmd-6.31.0/pmd_rules_java_codestyle.html#packagecase"                                     
        },                                                                                                                                    
        {                                                                                                                                     
          "beginline": 3,                                                                                                                     
          "begincolumn": 17,                                                                                                                  
          "endline": 7,                                                                                                                       
          "endcolumn": 1,                                                                                                                     
          "description": "All methods are static.  Consider using a utility class instead. Alternatively, you could add a private constructor or make the class abstract to silence this warning.",                                                                                         
          "rule": "UseUtilityClass",
          "ruleset": "Design",
          "priority": 3,
          "externalInfoUrl": "https://pmd.github.io/pmd-6.31.0/pmd_rules_java_design.html#useutilityclass"
        },
        {
          "beginline": 3,
          "begincolumn": 8,
          "endline": 7,
          "endcolumn": 1,
          "description": "The class name \u0027dd\u0027 doesn\u0027t match \u0027[A-Z][a-zA-Z0-9]*\u0027",
          "rule": "ClassNamingConventions",
          "ruleset": "Code Style",
          "priority": 1,
          "externalInfoUrl": "https://pmd.github.io/pmd-6.31.0/pmd_rules_java_codestyle.html#classnamingconventions"
        }
      ]
    }
  ],
  "suppressedViolations": [],
  "processingErrors": [],
  "configurationErrors": []
}
```

### cpd

```
./run.sh cpd --minimum-tokens 2 --files /home/tonglsh/IdeaProjects/demo-pmd/src
```



## maven-pmd-plugin

https://maven.apache.org/plugins/maven-pmd-plugin/

> The PMD Plugin allows you to automatically run the [PMD](https://pmd.github.io/) code analysis tool on your project's source code and generate a site report with its results. It also supports the separate Copy/Paste Detector tool (or CPD) distributed with PMD.
>
> This version of Maven PMD Plugin uses PMD 6.29.0 and requires Java 7. See [Upgrading PMD at Runtime](https://maven.apache.org/plugins/maven-pmd-plugin/examples/upgrading-PMD-at-runtime.html) for more information.
>
> The plugin accepts configuration parameters that can be used to customize the execution of the PMD tool.

### Version relationship between maven-pmd-plugin and PMD

Every maven-pmd-plugin version ships with a default PMD version. The default PMD version is upgraded irregularly, e.g. when support for a newer Java version is required.

Here's a historical overview about the default PMD version used:

| **maven-pmd-plugin**                                         | **PMD**                                        |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [3.14.0](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.14.0/) | [6.29.0](https://pmd.github.io/pmd-6.29.0/)    |
| [3.13.0](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.13.0/) | [6.21.0](https://pmd.github.io/pmd-6.21.0/)    |
| [3.12.0](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.12.0/) | [6.13.0](https://pmd.github.io/pmd-6.13.0/)    |
| [3.11.0](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.11.0/) | [6.8.0](https://pmd.sourceforge.io/pmd-6.8.0/) |
| [3.10.0](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.10.0/) | [6.4.0](https://pmd.sourceforge.io/pmd-6.4.0/) |
| [3.9.0](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.9.0/) | [6.0.1](https://pmd.sourceforge.io/pmd-6.0.1/) |
| [3.8](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.8/) | [5.6.1](https://pmd.sourceforge.io/pmd-5.6.1/) |
| [3.7](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.7/) | [5.5.1](https://pmd.sourceforge.io/pmd-5.5.1/) |
| [3.6](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.6/) | [5.3.5](https://pmd.sourceforge.io/pmd-5.3.5/) |
| [3.5](https://maven.apache.org/plugins-archives/maven-pmd-plugin-3.5/) | [5.3.2](https://pmd.sourceforge.io/pmd-5.3.2/) |

### Goals Overview

This plugin has 4 goals:

- [pmd:pmd](https://maven.apache.org/plugins/maven-pmd-plugin/pmd-mojo.html) creates a PMD site report based on the rulesets and configuration set in the plugin. It can also generate a pmd output file aside from the site report in any of the following formats: xml, csv or txt.
- [pmd:cpd](https://maven.apache.org/plugins/maven-pmd-plugin/cpd-mojo.html) generates a report for PMD's Copy/Paste Detector (CPD) tool. It can also generate a cpd results file in any of these formats: xml, csv or txt.
- [pmd:check](https://maven.apache.org/plugins/maven-pmd-plugin/check-mojo.html) verifies that the PMD report is empty and fails the build if it is not. This goal is executed by default when `pmd:pmd` is executed.
- [pmd:cpd-check](https://maven.apache.org/plugins/maven-pmd-plugin/cpd-check-mojo.html) verifies that the CPD report is empty and fails the build if it is not. This goal is executed by default when `pmd:cpd` is executed.

## Plugin Documentation



Goals available for this plugin:

| Goal                                                         | Report? | Description                                                  |
| :----------------------------------------------------------- | :------ | :----------------------------------------------------------- |
| [pmd:check](https://maven.apache.org/plugins/maven-pmd-plugin/check-mojo.html) | No      | Fail the build if there were any PMD violations in the source code. |
| [pmd:cpd](https://maven.apache.org/plugins/maven-pmd-plugin/cpd-mojo.html) | Yes     | Creates a report for PMD's CPD tool. See [Finding duplicated code](https://pmd.github.io/latest/pmd_userdocs_cpd.html) for more details. |
| [pmd:cpd-check](https://maven.apache.org/plugins/maven-pmd-plugin/cpd-check-mojo.html) | No      | Fail the build if there were any CPD violations in the source code. |
| [pmd:help](https://maven.apache.org/plugins/maven-pmd-plugin/help-mojo.html) | No      | Display help information on maven-pmd-plugin. Call `mvn pmd:help -Ddetail=true -Dgoal=` to display parameter details. |
| [pmd:pmd](https://maven.apache.org/plugins/maven-pmd-plugin/pmd-mojo.html) | Yes     | Creates a PMD report.                                        |

### System Requirements



The following specifies the minimum requirements to run this Maven plugin:

| Maven      | 3.0                     |
| ---------- | ----------------------- |
| JDK        | 1.7                     |
| Memory     | No minimum requirement. |
| Disk Space | No minimum requirement. |

### Usage



You should specify the version in your project's plugin configuration:

```xml
<project>
  ...
  <build>
    <!-- To define the plugin version in your parent POM -->
    <pluginManagement>
      <plugins>
        <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-pmd-plugin</artifactId>
          <version>3.14.0</version>
        </plugin>
        ...
      </plugins>
    </pluginManagement>
    <!-- To use the plugin goals in your POM or parent POM -->
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-pmd-plugin</artifactId>
        <version>3.14.0</version>
      </plugin>
      ...
    </plugins>
  </build>
  ...
  <!-- To use the report goals in your POM or parent POM -->
  <reporting>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-pmd-plugin</artifactId>
        <version>3.14.0</version>
      </plugin>
      ...
    </plugins>
  </reporting>
  ...
</project>
```

## alibaba-p3c

```xml
 <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-pmd-plugin</artifactId>
                <version>3.14.0</version>
                <configuration>
                    <sourceEncoding>utf-8</sourceEncoding>
                    <!-- cpd允许的重复行数 -->
                    <minimumTokens>1</minimumTokens>
                    <!-- pmd的告警等级(1~5) -->
                    <minimumPriority>3</minimumPriority>
                    <rulesets>
                        <!-- P3C-PMD implements 54 rules in 10 package 
						involved in Alibaba Java Coding Guidelines-->
                        <ruleset>rulesets/java/ali-comment.xml</ruleset>
                        <ruleset>rulesets/java/ali-concurrent.xml</ruleset>
                        <ruleset>rulesets/java/ali-constant.xml</ruleset>
                        <ruleset>rulesets/java/ali-exception.xml</ruleset>
                        <ruleset>rulesets/java/ali-flowcontrol.xml</ruleset>
                        <ruleset>rulesets/java/ali-naming.xml</ruleset>
                        <ruleset>rulesets/java/ali-oop.xml</ruleset>
                        <ruleset>rulesets/java/ali-orm.xml</ruleset>
                        <ruleset>rulesets/java/ali-other.xml</ruleset>
                        <ruleset>rulesets/java/ali-set.xml</ruleset>
                    </rulesets>
                </configuration>
                <dependencies>
                    <dependency>
                        <groupId>com.alibaba.p3c</groupId>
                        <artifactId>p3c-pmd</artifactId>
                        <version>2.1.1</version>
                    </dependency>
                </dependencies>
            </plugin>
        </plugins>
    </build>
```



## IDEA Plugin

*提供before commit,autofix,highlight*

https://github.com/alibaba/p3c/wiki/IDEA%E6%8F%92%E4%BB%B6%E4%BD%BF%E7%94%A8%E6%96%87%E6%A1%A3

## 自定义规则

https://github.com/pmd/pmd/releases

pmd-bin-【PMD 可执行版本】

- bin
  - designer.bat【界面工具，能将 java 源代码转化为 AST（抽象语法树），个人推荐使用】
  - bgastviewer.bat【界面工具，与 designer.bat 功能相似】
  - cpd.bat【用来查找重复代码的工具，命令行版】
  - cpdgui.bat【用来查找重复代码的工具，GUI 版】
  - pmd.bat【Window 平台下运行 PMD 需要使用的文件】
  - run.sh【Linux 平台下运行 PMD 需要使用的文件】
- lib【该目录存放 PMD 运行依赖的 jar 包，包括第三方 jar 包和各种语言的模块 jar 包】