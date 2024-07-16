# Demo App using IAS for Authentication to Approuter

This application is based on the sample application [demoAppRouter](https://github.com/SAP-samples/appgyver-auth-flows/tree/main/demoAppRouter).

## How to deploy things

```bash
mbt build
cf deploy mta_archives/demoApp_1.0.0.mtar
```

## Hybrid testing

```bash
cf create-service-key demoApp-uaa demoApp-uaa-key
cf create-service-key demoApp-ias demoApp-ias-key -c '{"credential-type":"X509_GENERATED"}'

cds bind -2 demoApp-uaa --for hybrid
cds bind identity -2 demoApp-ias --kind identity --for hybrid
```
