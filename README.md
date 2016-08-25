shibboleth-idp-gradle-overlay
=============================
The Shibboleth Identity Provider web application built using a Gradle overlay.

## Requirements

- JDK 8+
- Tomcat 8+

## Initial Setup

Run once:

```bash
./gradlew clean unpackShibboleth
```

## IntelliJ IDEA

Create a Run Configuration based on a Tomcat server. If you don't have a Tomcat instance available, download one as a zip archive and configure it inside IDEA. When done, select that as the application server in the Run Configuration screen.

### Server

- Specify a URL: `https://org.example.net:8443/idp`

- Add the following VM options:

```bash
-Didp.home=<project-path>/build/tmp/unpackShibboleth/shibboleth-idp
```

- For "Tomcat Server Settings", use ports `8080`, `8443` and `1099`.

- For "Before launch" tasks, add `build overlay`.

### Deployment

- Add an `External Source` for deployment, and select `<project-path>/build/tmp/unpackShibboleth/webapp`
- Use `/idp` as the application context path.

### Logs

- Select `Tomcat Localhost Log` and `Tomcat Catalina Log`
- Add a new log entry with the alias `idp` and the log file location `<project-path>/build/tmp/unpackShibboleth/shibboleth-idp/logs/idp-*.log`
