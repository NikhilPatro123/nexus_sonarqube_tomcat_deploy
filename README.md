

normal job
-------------------



Build Steps
Automate your build process with ordered tasks like code compilation, testing, and deployment.
Invoke top-level Maven targets
?

Maven Version

(Default)
Goals
clean package

Advanced
Nexus artifact uploader
Nexus Details
Nexus Version

NEXUS3
Protocol

HTTP
Nexus URL
?
3.6.36.248:8081
Credentials

admin/******
Add
GroupId
in.javahome
Version
8.7.8
Repository
?
app1
Artifacts
Artifact
ArtifactId
myweb
Type
?
.war
Classifier
?
File
?
target/myweb-8.7.8.war

Add
Add build step
Post-build Actions
Define what happens after a build completes, like sending notifications, archiving artifacts, or triggering other jobs.
Deploy war/ear to a container
WAR/EAR files
?
target/*.war
Context path
?
web-app
Containers
Tomcat 9.x Remote
Credentials

tomcat/******
Add
Tomcat URL
?
http://3.108.196.230:8080/
Advanced
Add Container

Deploy on failure
Add post-build action
