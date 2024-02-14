# oda-api-sdk-springboot
Building the ODA Open API SDK for Spring Boot.

## Tooling

1. Install [Open JDK](https://openjdk.org/projects/jdk/21/)
2. Install [OpenAPI Generator](https://openapi-generator.tech/docs/installation)
3. Install [Maven](https://maven.apache.org/download.cgi)

# Generate
Generate the ODA Open API stubs.

## [TMF676](https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.0.0/swagger/TMF676_Payment_Management_API_v4.0.0_swagger.json)
```bash
openapi-generator-cli generate \
	-g spring -o tmf676 \
	-i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.0.0/swagger/TMF676_Payment_Management_API_v4.0.0_swagger.json \
--additional-properties=\
groupId=com.odac,artifactId=paymentmgmt-svc,artifactDescription="TMF676 Payment Mgmt",\
name=paymentmgmt-svc,packaging=jar,useSpringBoot3=true,hideGenerationTimestamp=true,\
useSpringController=true,requestMappingMode=controller,\
basePackage=com.odac.tmfapi.tmf676,\
modelPackage=com.odac.tmfapi.tmf676.oapi.model,\
apiPackage=com.odac.tmfapi.tmf676.oapi.controller,\
configPackage=com.odac.tmfapi.tmf676.oapi.config
```
## Build and Run SDK
```bash
cd tmf676
mvn clean compile
mvn spring-boot:run
```
## Access Swagger UI Docs
http://localhost:8080/swagger-ui/index.html

## Run Examples
```bash
#Get all payments
curl -X GET "http://localhost:8080/payment/v4/payment" | json_pp

#Get payment by id
curl -X GET "http://localhost:8080/payment/v4/payment/e6358d3d-98eb-4af1-9d5e-2ecdccdccff1" | json_pp
```