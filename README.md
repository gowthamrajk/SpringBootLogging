# SpringBootLogging

- Spring Boot uses Apache Commons logging for all internal logging. 
- Spring Boot’s default configurations provides a support for the use of Java Util Logging, Log4j2, and Logback. 
- Using these, we can configure the console logging as well as file logging.
- If you are using Spring Boot Starters, Logback will provide a good support for logging. 
- Besides, Logback also provides a use of good support for Common Logging, Util Logging, Log4J, and SLF4J.

## Log Format

![image](https://user-images.githubusercontent.com/43011442/120165744-80742b80-c219-11eb-8802-4bdd33f15245.png)

This gives you information regarding the date and time of the log, Log level shows INFO, ERROR or WARN, Process ID, The --- which is a separator, Thread name is enclosed within the square brackets [], Logger Name that shows the Source class name, The Log message. 
