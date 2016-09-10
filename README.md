# CloudBrews-SampleApp

**Setup**
Start by making a directory and changing into it

```
mkdir sampleapp
cd sampleapp
```

**download the project**
```
git clone https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp
```

**build the project**
```
mvn install
```

**push it to pcf**
```
cf push attendees -p target/pcf-ers-demo1-0.0.1-SNAPSHOT.jar
```

**scale it, kill it**

**TBD**
- [ ] need to provision a database for the CloudBrews environment.  You were out of database instances.

**after binding a db to it**
```
cf restage attendees
```

**push version 2 with the same route**
```
cf push attendees-v2 -p target/pcf-ers-demo1-0.0.1-SNAPSHOT.jar
```

**copy the route from V1 to V2, scale down V1**
