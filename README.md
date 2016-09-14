## Station 3 - Sample App

##Introduction
In this excercise you will work with an already compleated sample applicaitons to learn more about cloud foundry.   Using the pre-built sample app you will do the following:  
  * Push the applicaiton to Pivotal Cloud Foundry
  * Scale the applicaiton so there are multiple instances running, and see how this make it fault tollerant
  * Make the app adhear to the 12 Factor design methodology by making the app store its state in a backing store rather than keeping it in the application context.
  * Blue-Green deploy a second copy of the applicaiton, by winding up instances of the new version, while winding down instances of the old version.

## Setup
Start by cleaning up after the last person and making a directory in your Google Compute Engine Console and changing into it. 
```
cd ~
rm -rf sampleapp
mkdir sampleapp
cd sampleapp
```

## Download the sample applicaiton from Github
```
git clone https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp
```


##Build the project
```
mvn install
```

##Push the sample application to pcf
```
cf login -a api.run.pivotal.io -u demo3@johnfunk.com -o Channel -s Denver-CloudBrews
cf push attendees -p target/pcf-ers-demo1-0.0.1-SNAPSHOT.jar
```

## Login to Cloud Foundry
Open cloud foundry in a browser by visiting:  http://run.pivotal.io  
   * username: demo3@johnfunk.com  
   * password:  ask one of the helpers  

##Navigate to the Application in Pivotal Cloud Foundry
First click on the 'Denver-CloudBrews' space as shown below:
![CloudFoundrySpace](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/CloudFoundrySpace.png "Space view on PCF")  

Next click on the link under the ROUTE lable as shown below:
![CloudFoundryApps](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/CloudFoundryApps.png "Apps view on PCF") 

 
## View the sample application in a browser
Open the following link in a browser: http://run.pivotal.io

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
