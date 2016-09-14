## Station 3 - Sample App

##Introduction
In this excercise you will work with an already compleated sample applicaitons to learn more about cloud foundry.   Using the pre-built sample app you will do the following:  
  * Push the applicaiton to Pivotal Cloud Foundry
  * Scale the applicaiton so there are multiple instances running, and see how this make it fault tollerant
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

Next click on the name of the "attendees" app shown below:
![CloudFoundryApps](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/CloudFoundryApps.png "Apps view on PCF") 

Then click on the "View App" link as shown below:
![CloudFoundryApps](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/CloudFoundryViewApp.png "Apps view on PCF") 

This will take you to the sample app.  Once in the app click on the "basic" link as shown below:
![CloudFoundryApps](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/SampleAppScreen1.png "Run the basic app") 

This sample app has a built in load test.  To run it click on the "Start Load Test" link as shown below:
![CloudFoundryApps](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/SampleAppScreen2.png "Start the load test") 
 
## Scale the App
Next you will scale the application up, to do that go back to the Pivotal Cloud Foundry window in the browser and scale the app as shown below:
![CloudFoundryApps](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/SampleAppScreen3.png "Scale the App on PCF") 

Then return to the application tab in the browser and look at the load test.  It should show you are running 2 instances of the app. 
![CloudFoundryApps](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/SampleAppScreen4.png "Scale the App on PCF") 

## Blue/Green Deployment 
Next you will use Blue/Green deployment style to deploy a new version of the application.  To learn more about Blue/Green Deployment read the description provided in the application. Following the steps below:
![CloudFoundryApps](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/SampleAppBlueGreen1.png "Switch to blue/green page") 

![CloudFoundryApps](https://github.com/JohnFunk-Pivotal/CloudBrews-SampleApp/blob/master/SampleAppBlueGreen2.png "Read about Blue/Green Deployment") 


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
