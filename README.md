# bookstore


Install the reusable service project as npm dependency:
```
npm install $(npm pack ../products-service -s)
```

Install all other packages and simplify the overall dependency structure
```
npm install && npm dedupe
```

## deploy on SAP BTP

https://developers.sap.com/tutorials/cp-cap-java-deploy-cf.html

Enhance project configuration for production
```
cds add hana,mta,xsuaa,approuter --for production
```

### deploy using cf deploy

Need to provision SAP HANA Cloud instance, which is a prerequisite to later on create a SAP HANA HDI Container to deploy your database artifacts to.

Follow the tutorial [Provision an Instance of SAP HANA Cloud (Step 1+2)](https://developers.sap.com/tutorials/hana-cloud-mission-trial-2.html). Make sure to allow access to SAP HANA Cloud from all IPs and that the instance of the SAP HANA you have created is[ mapped to your subaccount and space](https://developers.sap.com/tutorials/hana-cloud-mission-trial-8.html) (Step 1) where you working with this tutorial.

```
mbt build -t gen --mtar mta.mtar
cf deploy gen/mta.mtar
```