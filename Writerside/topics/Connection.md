# Connection

To store data about connecting to AccelQ, we use public Custom Settings.
Here we store Api Key, Tenant Code, Url, Username.
![](accelq-connection-custom-settings.png)

Also, before connecting to AccelQ, we create Remote Site Settings in the organization using Apex.
```java
    @AuraEnabled
    public static void createRemoteSiteSetting(String endpointUrl) {
        if (MetadataUtils.checkDuplicateRemoteSiteSettings(endpointUrl)) {
            return;
        } else {
            MetadataUtils.createRemoteSiteSettings(endpointUrl, 'accelq' + Math.abs(endpointUrl.hashCode()));
        }
    }
```
