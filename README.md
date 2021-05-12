# Handling Slowly Changing Dimensions With Azure Synapse Analytics Pipelines
This file contains text you can copy and paste for the examples in Cloud Academy's _Handling Slowly Changing Dimensions With Azure Synapse Analytics Pipelines_ course.  

### Introduction
[Azure Free Trial](https://azure.microsoft.com/free) 

### Creating the Data Flow
HashKey expression: 
```
sha2(256, iifNull(Title,'') +FirstName +iifNull(MiddleName,'') +LastName +iifNull(Suffix,'') +iifNull(CompanyName,'') +iifNull(SalesPerson,'') +iifNull(EmailAddress,'') +iifNull(Phone,''))
```
InsertedDate expression:
```
iif(isNull(InsertedDate), currentTimestamp(), {InsertedDate})
```
ModifiedDate expression:
```
currentTimestamp()
```

### Running the Data Flow
```
SELECT * from dbo.CustomerSink WHERE CustomerId = 4
```
```
UPDATE dbo.CustomerSource
SET LastName = 'Lopez'
WHERE CustomerId = 4
```

### Summary
[Azure Synapse Analytics documentation](https://docs.microsoft.com/azure/synapse-analytics/)  
support@cloudacademy.com
