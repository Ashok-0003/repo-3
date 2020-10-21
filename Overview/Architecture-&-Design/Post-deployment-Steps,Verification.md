Update APIM policy for

1. Get all features and their values.
1. Get the value for the key given in settings.

```
<policies>
   <inbound>
        <base />
        <cache-lookup vary-by-developer="false" vary-by-developer-groups="false" downstream-caching-type="none">
            <vary-by-header>Accept</vary-by-header>
            <vary-by-header>Accept-Charset</vary-by-header>
            <vary-by-header>Authorization</vary-by-header>
        </cache-lookup>
    </inbound>
    <backend>
        <base />
    </backend>
    <outbound>
        <base />
        <cache-store duration="2" />
    </outbound>
    <on-error>
        <base />
    </on-error>
</policies>
```