# medical-appointment-scheduling-server

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=PrimeDominus_medical-appointment-scheduling-server&metric=alert_status)](https://sonarcloud.io/dashboard?id=PrimeDominus_medical-appointment-scheduling-server)
[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=PrimeDominus_medical-appointment-scheduling-server&metric=vulnerabilities)](https://sonarcloud.io/dashboard?id=PrimeDominus_medical-appointment-scheduling-server)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=PrimeDominus_medical-appointment-scheduling-server&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=PrimeDominus_medical-appointment-scheduling-server)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=PrimeDominus_medical-appointment-scheduling-server&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=PrimeDominus_medical-appointment-scheduling-server)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=PrimeDominus_medical-appointment-scheduling-server&metric=security_rating)](https://sonarcloud.io/dashboard?id=PrimeDominus_medical-appointment-scheduling-server)

## Features
* Provides data models required for [sebastianhaas/medical-appointment-scheduling](https://github.com/sebastianhaas/medical-appointment-scheduling)
* REST API
 * including a web-based API explorer mounted at http://0.0.0.0:3000/explorer
 * produces swagger API defintion
* WebSocket for CTI (Computer Telephony Integration) support using [CantyCTI](https://github.com/sebastianhaas/cantycti)
* Unit tested
* Rich test data generation

## Local setup
Clone this repository and run 
```shell
$ npm install
```
with a postgres database set up according to the [`datasources.json`](https://github.com/sebastianhaas/medical-appointment-scheduling-server/blob/master/server/datasources.json) config file running, start the server using
```shell
$ npm start
```
You might want to set up a dummy mail server for Email notification to work locally. Configuration can be found in [`datasources.json`](https://github.com/sebastianhaas/medical-appointment-scheduling-server/blob/master/server/datasources.json).

Browse to http://localhost:3000/explorer to take a look on the API using the explorer. Test data can be added using the respective endpoints:
```shell
# Start with:
post /Examinations/insertTestData
post /Patients/insertTestData
post /Rooms/insertTestData

# Afterwards:
post /appointments/generateRandomAppointments 

# And finally:
post /Attendances/generateRandomAttendances
```
Some of these endpoints have an optional `locale` parameter to generate test data appropriate for a specific locale (currently only `de` and `en`). Just use the API explorer to find out about it.
