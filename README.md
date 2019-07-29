# settings
Development app or program, using resources : Properties, Settings, Command, any else.



### Usage

- When you launch a app on the linux.

- If you want to start spring app, it could be help you.



### For Linux

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

- Install tomcat on the linux. ' [3. [centOS7] 톰캣(Tomcat) 설치](https://goddaehee.tistory.com/74) '

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

- application.properties

  ```
  # MySQL JPA settings
  spring.jpa.database-platform=org.hibernate.dialect.MySQL5Dialect
  spring.jpa.show-sql=false
  spring.jpa.hibernate.ddl-auto=create
  
  # MSSQL DB Settings
  spring.dataSource.url=jdbc:jtds:sqlserver://localhost:3308;databaseName=Test_web
  spring.datasource.driver-class-name=net.sourceforge.jtds.jdbc.Driver
  # DB connection info
  spring.datasource.username=sa
  spring.datasource.password=123456
  
  # MySQL | Maria DB Settings
  spring.datasource.url=jdbc:mysql://localhost:3308/web_project?autoReconnect=true&serverTimezone=UTC
  spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
  # DB connection info
  spring.datasource.username=root
  spring.datasource.password=123456
  
  #Oracle
  spring.datasource.url=jdbc:oracle:thin:@localhost:3306:test
  spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
  spring.datasource.username=scott
  spring.datasource.password=tiger
  
  # prefix on spring-boot. ordinary spring want to use prefix, write other xml.
  spring.mvc.view.prefix=/WEB-INF/jsp/
  spring.mvc.view.suffix=.jsp
  
  ```

- Maven update -> install -> run or build (war)
- Confirm the program on local then upload your server.  (local -> Dev -> SIT -> PRD)



