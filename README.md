# fhir-hapi-jumpstart
Docker compose and configurations to run a FHIR HAPI server to connect to with your android Application running the Android FHIR SDK!

### Server setup
1. Install Docker Desktop https://www.docker.com/products/docker-desktop
2. Clone this repository `git clone https://github.com/Apra-Labs/fhir-hapi-jumpstart`
3. Open cmd and cd into the repo directory
4. Run ipconfig and copy your IPv4 Address. It will look something like this `IPv4 Address. . . . . . . . . . . : 192.168.1.1`
5. Open the data/hapi/application.yaml and edit the line server_address to set the domain to the ip address from the command above.
6. Run `docker compose up`
7. Check the hapi-fhir-server continer logs from docker desktop, if it throws a cannot connect to db exception, restart it. 

### Android client set up
1. Install android studio
2. clone https://github.com/google/android-fhir `git clone https://github.com/google/android-fhir`
3. Edit `demo/src/main/java/com/google/android/fhir/demo/FhirApplication.kt` file with your ip address.

Example:
```
ServerConfiguration(
    "https://192.168.1.1:8085/",
    httpLogger =
        HttpLogger(
            HttpLogger.Configuration(
                if (BuildConfig.DEBUG) HttpLogger.Level.BODY else HttpLogger.Level.BASIC
            )
        ) { Timber.tag("App-HttpLog").d(it) }
    )
```

4. Edit `demo/src/main/res/xml/network_security_config.xml` file with your ip address.

Example:
```
<?xml version="1.0" encoding="utf-8" ?>
<network-security-config>
    <domain-config cleartextTrafficPermitted="true">
        <domain includeSubdomains="true">192.168.1.1</domain>
    </domain-config>
</network-security-config>
```
