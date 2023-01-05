# fhir-hapi-jumpstart
Docker compose and configurations to run a FHIR HAPI server to connect to with your android Application running the Android FHIR SDK!

### Android client set up
1. Install android studio
2. clone https://github.com/google/android-fhir `git clone https://github.com/google/android-fhir`
3. Edit `demo/src/main/res/xml/network_security_config.xml` file with your ip address.

Example:
```
<?xml version="1.0" encoding="utf-8" ?>
<network-security-config>
    <domain-config cleartextTrafficPermitted="true">
        <domain includeSubdomains="true">192.168.1.1</domain>
    </domain-config>
</network-security-config>
```
