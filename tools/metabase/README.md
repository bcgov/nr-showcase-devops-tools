# Metabase

This folder contains the OpenShift templates required in order to build and deploy an instance of Metabase onto OpenShift. These templates were designed with the assumption that you will be building and deploying the Metabase application within the same project. We will be running with the assumption that this Metabase instance will be co-located in the same project as the database it is expecting to poll from.

## Build Metabase

While Metabase does provide a Docker image [here](https://hub.docker.com/r/metabase/metabase), it is not compatible with OpenShift due to the image assuming it has root privileges. Instead, we build a simple Java image based off of Alpine JDK 8 where the metabase application can execute without needing privilege escalation. In order to build a Metabase image in your project, process and create the build config template using the following command (replace anything in angle brackets with the correct value):

``` sh
oc process -n <namespace> -f metabase.bc.yaml -o yaml | oc create -n <namespace> -f -
```

This will create two ImageStreams: `openjdk` and `metabase`. OpenJDK is the base java image that will be built on, and metabase is the finished image build.

## Deploy Metabase

Once your metabase image has been successfully built, you can then deploy it in your project by using the following command (replace anything in angle brackets with the correct value):

``` sh
oc process -n <namespace> -f metabase.dc.yaml ADMIN_EMAIL=<youremailhere> NAMESPACE=<namespace> -o yaml | oc create -n 9f0fbe-prod -f -
```

This will create a new Secret, Service, Route, Persistent Volume Claim, and Deployment Configuration. This Deployment Config has liveliness and readiness checks built in, and handles image updates via Recreation strategy. A rolling update cannot work because the H2 database is locked by the old running pod and prevents the newer instance of Metabase from starting up.

## Initial Setup

Once Metabase is up and functional (this will take between 3 to 5 minutes), you will have to do initial setup manually. We suggest you populate the email account and password as whatever the `metabase-secret` secret contains in the `admin-email` and `admin-password` fields respectively. You may be asked to connect to your existing Postgres (or equivalent) database during this time, so you will need to refer to your other secrets or other deployment secrets in order to ensure Metabase can properly connect to it via JDBC connection.

## Notes

In general, Metabase should generally take up very little CPU (<0.01 cores) and float between 700 to 800mb of memory usage during operation. The template has some reasonable requests and limits set for both CPU and Memory, but you may change it should your needs be different. For some more documentation referencees, you may refer [here](https://github.com/loneil/domo-metabase-viewer/tree/master/docs) for historical templates and tutorials, or inspect the official Metabase documentation [here](https://www.metabase.com/docs/latest/).
