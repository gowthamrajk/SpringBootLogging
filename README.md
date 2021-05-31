# SpringBootLogging

- Spring Boot uses Apache Commons logging for all internal logging. 
- Spring Boot’s default configurations provides a support for the use of Java Util Logging, Log4j2, and Logback. 
- Using these, we can configure the console logging as well as file logging.
- If you are using Spring Boot Starters, Logback will provide a good support for logging. 
- Besides, Logback also provides a use of good support for Common Logging, Util Logging, Log4J, and SLF4J.

## Log Format

![image](https://user-images.githubusercontent.com/43011442/120165744-80742b80-c219-11eb-8802-4bdd33f15245.png)

This gives you information regarding the date and time of the log, Log level shows INFO, ERROR or WARN, Process ID, The --- which is a separator, Thread name is enclosed within the square brackets [], Logger Name that shows the Source class name, The Log message. 

## Console Log

- The default log messages will print to the console window. 
- By default, “INFO”, “ERROR” and “WARN” log messages will print in the log file.
- add the debug mode to your application.properties file as **debug = true**

## File Log

- By default, all logs will print on the console window and not in the files. 
- If you want to print the logs in a file, you need to set the property **logging.file** or **logging.path** in the **application.properties** file.
- specify the log file path using the property as **logging.path = /var/tmp/**
- specify the own log file name using the property as **logging.file = /var/tmp/mylog.log**
**Note** − Logback does not support **“FATAL”** level log. It is mapped to the **“ERROR”** level log.

## Configuring LogBack

- Logback supports XML based configuration to handle Spring Boot Log configurations. 
- Logging configuration details are configured in **logback.xml** file. 
- The **logback.xml** file should be placed under the classpath.

configure the ROOT level log in **Logback.xml** file as 

    <?xml version = "1.0" encoding = "UTF-8"?>
    <configuration>
       <root level = "INFO">
       </root>
    </configuration>

configure the console appender in **Logback.xml** file as

    <?xml version = "1.0" encoding = "UTF-8"?>
    <configuration>
       <appender name = "STDOUT" class = "ch.qos.logback.core.ConsoleAppender"></appender>
       <root level = "INFO">
          <appender-ref ref = "STDOUT"/> 
       </root>
    </configuration>

configure the file appender in **Logback.xml** file as

    <?xml version = "1.0" encoding = "UTF-8"?>
    <configuration>
       <appender name = "FILE" class = "ch.qos.logback.core.FileAppender">
          <File>...path</File>
       </appender>   
       <root level = "INFO">
          <appender-ref ref = "FILE"/>
       </root>
    </configuration>
    
Define the Log pattern in **logback.xml** file as

    <pattern>[%d{yyyy-MM-dd'T'HH:mm:ss.sss'Z'}] [%C] [%t] [%L] [%-5p] %m%n</pattern>
    
Complete logback.xml file with the rest of you logical code...

**[refer in my application's Logbackxml file for more code]**

## use of .yml file

- Using yml file, you can define log levels of Spring Boot loggers, application loggers, Hibernate loggers, Thymeleaf loggers, and more. 
- To set the logging level for any logger, add keys starting with logging.level. 
- Logging level can be one of one of **TRACE** , **DEBUG** , **INFO** , **WARN** , **ERROR** , **FATAL** , **OFF**

configure the **application.yml** file as

    logging:
      level:
        org.springframework.web: ERROR
        com.application: DEBUG
      pattern:
        console: '%d{yyyy-MM-dd HH:mm:ss} - %msg%n'
        file: '%d{yyyy-MM-dd HH:mm:ss} [%thread] %-5level %logger{36} - %msg%n'
      file: C:\Users\Windows\spring-boot-logging\api.log
      
The last line in .yml configuration file is to mention the path in our system where the logged file has to e stored.

## Adding SLF4J logger in applicaion

