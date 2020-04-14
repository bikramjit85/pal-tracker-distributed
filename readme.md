cf create-service p.mysql db-small tracker-allocations-database

cf create-service p.mysql db-small tracker-backlog-database

cf create-service p.mysql db-small tracker-registration-database

cf create-service p.mysql db-small tracker-timesheets-database
 
 1. Deploying a Distributed System

 gradlew cloudNativeDeveloperDistributedSystemDeployment -PregistrationServerUrl=https://registration-pal-bikram-paltrackdist-arch1.cfapps.io -PbacklogServerUrl=https://backlog-pal-bikram-paltrackdist-arch1.cfapps.io    -PallocationsServerUrl=https://allocations-pal-bikram-paltrackdist-arch1.cfapps.io    -PtimesheetsServerUrl=https://timesheets-pal-bikram-paltrackdist-arch1.cfapps.io
 
 2.
 
 cf create-service p-service-registry standard tracker-service-registry
 
 3. Circuit Breaker

  gradlew cloudNativeDeveloperDistributedSystemWithCircuitBreaker -PregistrationServerUrl=https://registration-pal-bikram-paltrackdist-arch1.cfapps.io -PbacklogServerUrl=https://backlog-pal-bikram-paltrackdist-arch1.cfapps.io    -PallocationsServerUrl=https://allocations-pal-bikram-paltrackdist-arch1.cfapps.io    -PtimesheetsServerUrl=https://timesheets-pal-bikram-paltrackdist-arch1.cfapps.io
  
4 Securing a Distributed System

cf create-service p-identity pal tracker-sso

 gradlew cloudNativeDeveloperDistributedSystemWithSecurity -PuaaUrl=https://pal.login.run.pivotal.io    -PclientId=ccfbee3e-2e61-4778-a5a7-17e710f87c3a   -PclientSecret=2a7f7b73-c554-4bd4-8e9b-6f35d69af4be  -PregistrationServerUrl=https://registration-pal-bikram-paltrackdist-arch1.cfapps.io -PbacklogServerUrl=https://backlog-pal-bikram-paltrackdist-arch1.cfapps.io    -PallocationsServerUrl=https://allocations-pal-bikram-paltrackdist-arch1.cfapps.io    -PtimesheetsServerUrl=https://timesheets-pal-bikram-paltrackdist-arch1.cfapps.io
 
 5. Config Server
cf create-service p-config-server standard tracker-config-server -c "{\"git\": {\"uri\": \"https://github.com/${YOUR_GITHUB_USERNAME}/tracker-config.git\", \"label\": \"master\"}}"

 gradlew cloudNativeDeveloperDistributedSystemWithSecurity  -PuaaUrl=https://pal.login.run.pivotal.io    -PclientId=ccfbee3e-2e61-4778-a5a7-17e710f87c3a   -PclientSecret=2a7f7b73-c554-4bd4-8e9b-6f35d69af4be  -PregistrationServerUrl=https://registration-pal-bikram-paltrackdist-arch1.cfapps.io -PbacklogServerUrl=https://backlog-pal-bikram-paltrackdist-arch1.cfapps.io    -PallocationsServerUrl=https://allocations-pal-bikram-paltrackdist-arch1.cfapps.io    -PtimesheetsServerUrl=https://timesheets-pal-bikram-paltrackdist-arch1.cfapps.io