cf create-service p.mysql db-small tracker-allocations-database

cf create-service p.mysql db-small tracker-backlog-database

cf create-service p.mysql db-small tracker-registration-database

cf create-service p.mysql db-small tracker-timesheets-database
 
 1. Deploying a Distributed System

 gradlew cloudNativeDeveloperDistributedSystemDeployment -PregistrationServerUrl=https://registration-pal-bikram-paltrackdist-arch1.cfapps.io -PbacklogServerUrl=https://backlog-pal-bikram-paltrackdist-arch1.cfapps.io    -PallocationsServerUrl=https://allocations-pal-bikram-paltrackdist-arch1.cfapps.io    -PtimesheetsServerUrl=https://timesheets-pal-bikram-paltrackdist-arch1.cfapps.io
 
 2.
 
 cf create-service p-service-registry standard tracker-service-registry