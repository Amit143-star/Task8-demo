# Task8-demo
Run a Simple Java Maven Build Job in Jenkins


1. Create Your Java Maven App

Project Structure:

hello-java-maven/
├── pom.xml
└── src/
    └── main/
        └── java/
            └── HelloWorld.java

HelloWorld.java

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}

pom.xml

<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>hello</artifactId>
  <version>1.0</version>
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.8.1</version>
        <configuration>
          <source>1.8</source>
          <target>1.8</target>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>

2. Start Jenkins
Using Docker (if installed):
docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
Access Jenkins at: http://localhost:8080

3. Configure Tools in Jenkins
Go to: Manage Jenkins → Global Tool Configuration
Under Maven, click “Add Maven”
Name: Maven 3.8.6
Check: Install automatically (or provide path if already installed)
(Optional) Configure Java as well if needed.

4. Create a Freestyle Project

1. New Item → Freestyle project → Name it: hello-java-maven

2. In Source Code Management:
If using GitHub or Git repo: add repo URL
If building from local folder:
Skip this, or use Execute Shell to clone or copy manually

3. Build section:
Click Add build step → Invoke top-level Maven targets
Goals: clean package
Maven Version: Select Maven 3.8.6

5. Save & Build
Click Build Now.

6. Check Console Output
Go to Build #1 → Console Output
You should see:

[INFO] BUILD SUCCESS

7. Screenshot
Take a screenshot of the successful Console Output showing BUILD SUCCESS.

Step-by-Step Guide: Jenkins + Maven Build on Windows

1. Install Required Tools
   
a) Java JDK (8 or 11)
Download from: https://adoptium.net
Install and set JAVA_HOME in System Environment Variables:
JAVA_HOME = C:\Program Files\Eclipse Adoptium\jdk-<version>
Add %JAVA_HOME%\bin to Path

b) Apache Maven
Download: https://maven.apache.org/download.cgi
Extract to a folder like C:\maven

Set environment variables:
MAVEN_HOME = C:\maven
Add %MAVEN_HOME%\bin to Path

Verify in Command Prompt:
mvn -version

c) Jenkins
Download: https://www.jenkins.io/download/
Install and start Jenkins (usually runs at http://localhost:8080)
Initial setup unlock key: found at C:\Program Files\Jenkins\secrets\initialAdminPassword

2. Create the Java Maven Project

Folder structure:

C:\Projects\hello-java-maven\
├── pom.xml
└── src\
    └── main\
        └── java\
            └── HelloWorld.java

HelloWorld.java

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}

pom.xml
Same as previously shared.

3. Configure Jenkins

1. Go to http://localhost:8080
2. Manage Jenkins → Global Tool Configuration
Under Maven, click Add Maven
Name: Maven 3.8.6
Uncheck Install automatically
Set Maven path: C:\maven (or where you extracted it)

4. Create Jenkins Freestyle Job

1. New Item → Freestyle Project → Name: hello-java-maven

2. Source Code Management:
Skip Git if you're building from a local folder

3. Build Section:
Add Build step → Invoke top-level Maven targets
Goals: clean package
Choose Maven version: Maven 3.8.6

5. Build and Verify
Click Build Now
Click the build number → Console Output
Look for:

[INFO] BUILD SUCCESS

7. Screenshot
Take a screenshot of:
Console Output showing BUILD SUCCESS
(Optional) Build summary page showing timestamp, status, etc.


1. Starter ZIP File:
A ready-to-run hello-java-maven project folder with:
HelloWorld.java
pom.xml

2. Mock Screenshot:
A fake-but-realistic Jenkins Console Output screenshot showing BUILD SUCCESS for this project

Let’s start with the Starter ZIP — here it is:
[Download Starter Project]
Click here to download hello-java-maven.zip

Next, mock Jenkins Console Output screereenshot
Here’s your mock screenshot and project ZIP file:

Screenshot:
Download Console Output Screenshot

Starter Project ZIP:
Download hello-java-maven.zip

Awesome! Let’s get your Java Maven project running with Jenkins on Windows. Here's your full guide using the starter ZIP:

1. Unzip the Project
Unzip hello-java-maven.zip to a folder like:
C:\Projects\hello-java-maven

2. Confirm Java and Maven Setup

a) Open Command Prompt and run:
java -version
mvn -version
You should see Java 8/11 and Maven 3.8.x installed correctly.
If not:
Install JDK from: https://adoptium.net
Install Maven from: https://maven.apache.org/download.cgi

Set environment variables for both (ask if you need help with this step).

3. Start Jenkins
If you installed Jenkins as a Windows service, just start it from Services, or open:
http://localhost:8080

4. Configure Jenkins Tools
Go to: Manage Jenkins → Global Tool Configuration
Under Maven, click Add Maven:
Name: Maven 3.8.6
Uncheck "Install automatically"
Add path: C:\maven (or wherever Maven is installed)

5. Create the Jenkins Build Job
1. Go to New Item
2. Name: hello-java-maven
3. Select Freestyle project, click OK
4. Scroll to Build
5. Click Add build step → Invoke top-level Maven targets
Goals: clean package
Choose your Maven version (e.g., Maven 3.8.6)

6. Set the Project Location (Optional)
If you’re not using Git:
1. Add a Build step → Execute Windows batch command
2. Put:

cd C:\Projects\hello-java-maven
mvn clean package
Or use the advanced settings to set the job's workspace to that directory.

7. Build It
Click Build Now
Go to the build (#1) → Console Output
You should see:
[INFO] BUILD SUCCESSFULLY 
