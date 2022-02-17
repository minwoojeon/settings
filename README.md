# Version
2022.02.17. 최신화
- 영어로 있어 보이려고 하던 거는 집어 치우고 한글로 적습니다.

# settings
- 여기에 들어가는 것은 일반적인 세팅이 아닙니다.
- 그렇다고 엄청 특수한거는 또 아니고, 제가 그냥 아~ 이런게 있구나 하는 것들을 실무하면서 채워 나가는 것들입니다.

### Usage
- 그 뭐 굳이 실행해 보고 싶으시면 리눅스나 맥에서 아니면 윈도우 파워 쉘에서 작성해 보면 되긴 하는데, 일부 의존성이 있을 수 있으니 필요하신 거나 문의 사항은 저한테 문의주세요.

### 리눅스 VM 에서 이것저것 터미널 명령어
- 이 부분은 보니까 과거의 제가 아주 기본적인 부분을 뭔가 폴더나 파일 만드는거나 이런거 쓴 거 같은데, 수정이 아니라 추가형태로 작성을 합니다.
- 굳이 VM 이 아니어도 되고 터미널 명령이랑 권한만 된다면 다 되는 명령입니다.
- Install programs for remote control-OS : [putty](https://putty.org/), [filezilla](https://filezilla-project.org/).
- Command list

  ```command shell
  -- Checking linux login log
  cat /var/log/secure* | grep Accepted | awk 'IP' | sort | uniq
  -- example
  cat /var/log/secure* | grep Accepted | awk '123.45.6.78' | sort | uniq
  -- if you want to denided user log, this
  cat /var/log/secure* | grep Failed | awk '123.45.6.78' | sort | uniq
  
  -- Manage user mode
  -- confirm user list
  cat /etc/passwd
  -- Add user - or you want to allow another accept account - in your server then
  useradd -d /nfs_mnt -g 1001 test
  -- useradd command option d : default directory, g : include groups.
  -- Add password.
  passwd readTeam
  
  -- Clear on your command Line, like a 'cls'
  clear
  
  -- File or directory manage
  -- mkdir / rm
  mkdir test
  cd test
  ls
  -- make a file or write
  -- no one > is confirm file, > one : over-write, >> two : countinues-write 
  cat >> ./test
  hi, mrs botbinoo.
  ^Z
  cat test
  -- if you want to confirm to file on real-time,
  tail -f test
  -- rm file or directory.
  rm ./test
  
  -- tar is unzip command
  tar fileName
  ```

- Install brew on the linux. ' [centOS에 brew 설치하기](https://cuter74.tistory.com/35)'

- Install open-java. ' [bugtype mySetting](https://github.com/bugtype/mySetting) '
- (2022.02.17. 꼭 open-jdk 설치를 안해도 됩니다. 원하는 버전으로 받아서 설치하거나 일부 개발자들은 의존성 라이브러리를 자신의 하드나 usb, 심지어 git에 찾아보면 pom.xml 이나 gradle 로 내려 받기도 하기 때문에 굳이 open-jdk 쓰세요! 라는 말은 좋지 않을 것 같네요.)

- Install tomcat on the linux. ' [3. [centOS7] 톰캣(Tomcat) 설치](https://goddaehee.tistory.com/74) '
- (2022.02.17. 이게 빌드시 내장하도록 빌드하면 톰캣 설치를 안해도 됩니다. war 빌드 하지말고 jar 로 빌드하게 한 다음 서버에서는 jar 를 실행시키고 nginx 같은 웹 서버가 프록시만 받으면 됩니다. 톰캣을 설치해서 가는 경우는 war 배포와 동시에 빌드시 서버 내장을 안하겠다 정도입니다. 아울러 굳이 톰캣이 아니어도 됩니다.)

  ```command shell
  -- step 1. Move directory
  cd /test
  -- step 2. get tar or rpm
  wget http://archive.apache.org/dist/tomcat/tomcat-8/v8.5.27/bin/apache-tomcat-8.5.27.tar.gz
  -- step 3. unzip
  tar xvfz apache-tomcat-8.5.27.tar.gz
  -- step 4. confirm global-path 
  vi /etc/profile
  -- java_home, jre_home, catalina_home, classpath
  source /etc/profile
  -- step 5. turn on/off tomcat
  /test/apache-tomcat-8.5.27/bin/startup.sh
  /test/apache-tomcat-8.5.27/bin/shutdown.sh
  ```

- If you want to restart server, then

  ```command shell
  -- step 1. shutdown server.
  /test/apache-tomcat-8.5.27/bin/shutdown.sh
  -- step 2. move your app on the server. : war or jsp or html or etc.
  -- step 3. startup server.
  /test/apache-tomcat-8.5.27/bin/startup.sh
  ```

- If you want to add environment-variables

  ```
  -- HOST-NAME is not same
  JAVA_HOME=/home/HOST-NAME/html/bf/java-se-8u40-ri
  JRE_HOME=/home/HOST-NAME/html/bf/java-se-8u40-ri/jre
  CATALINA_HOME=/home/HOST-NAME/html/bf/apache-tomcat-8.5.43
  CLASSPATH=.:$JAVA_HOME/lib/tools.jar:$CATALINA_HOME/lib/jsp-api.jar:$CATALINA_HO
  ME/lib/servlet-api.jar
  PATH=$PATH:$JAVA_HOME/bin:$CATALINA_HOME/bin
  export JAVA_HOME CLASSPATH CATALINA_HOME JRE_HOME
  ```


### For Spring-app

- Install programs for local-IDE : Eclipse, IntellJ

- dependencies : pom.xml

  ```
  <!-- 1. 전자정부 framwork. -->
  	<repositories>
  	...
  		<repository>
  			<id>egovframe</id>
  			<!-- 전자정부 maven repository -->
  			<url>http://maven.egovframe.kr:8080/maven/</url>
  			<releases>
  				<enabled>true</enabled>
  			</releases>
  			<snapshots>
  				<enabled>false</enabled>
  			</snapshots>
  		</repository>
  	</repositories>
  <!-- 2. maven repository 홈페이지에서 나머지들은 받으면 됨. -->
  ```
- (2022.02.17. 이거 이제 http 안됩니다. 에러납니다. https 로 해야합니다.)

- application.properties

  ```
  # MySQL JPA settings
  spring.jpa.database-platform=org.hibernate.dialect.MySQL5Dialect
  spring.jpa.show-sql=false
  spring.jpa.hibernate.ddl-auto={ none | create | create-drop | update | validate }
  
  # MSSQL DB Settings
  spring.dataSource.url=jdbc:jtds:sqlserver://localhost:3308;databaseName=Test_web
  spring.datasource.driver-class-name=net.sourceforge.jtds.jdbc.Driver
  # DB connection info
  spring.datasource.username={username}
  spring.datasource.password={userpassword}
  
  # MySQL | Maria DB Settings
  spring.datasource.url=jdbc:mysql://localhost:3308/web_project?autoReconnect=true&serverTimezone=UTC
  spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
  # DB connection info
  spring.datasource.username={username}
  spring.datasource.password={userpassword}
  
  #Oracle
  spring.datasource.url=jdbc:oracle:thin:@localhost:3306:test
  spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
  spring.datasource.username={username}
  spring.datasource.password={userpassword}
  
  # prefix on spring-boot. ordinary spring want to use prefix, write other xml.
  spring.mvc.view.prefix=/WEB-INF/jsp/
  spring.mvc.view.suffix=.jsp
  
  ```

- Maven update -> install -> run or build (war)
- Confirm the program on local then upload your server.  (local -> Dev -> SIT -> PRD)



