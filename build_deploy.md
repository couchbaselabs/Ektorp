
# To build the project:

$ mvn

# To update the version number

Edit:

     - pom.xml
     - org.ektorp/pom.xml
     - org.ektorp.android/pom.xml

to have the new version number

# To deploy the artifact to nexus

## Edit pom.xml to not build ektorp spring

Under modules, remove

 * org.ektorp.spring

## Edit pom.xml to have repo url

Under `<distributionManagement>`:

```
		<repository>
			<id>deployment</id>
			<name>Couchbase Nexus Repository</name>
			<url>http://maven.hq.couchbase.com/nexus/content/repositories/releases/</url>
		</repository>
```

## Create ~/.m2/settings.xml

Example:

```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <localRepository/>
  <interactiveMode/>
  <usePluginRegistry/>
  <offline/>
  <pluginGroups/>
  <servers>
  <server>
    <id>deployment</id>
    <username>deployment</username>
    <password>password</password>
  </server>
</servers>

  <mirrors/>
  <proxies/>
  <profiles/>
  <activeProfiles/>
</settings>
```

## Run mvn deploy

```
$ mvn deploy
```

# To deploy the artifact to files.couchbase.com 

Manually copy from Nexus 

