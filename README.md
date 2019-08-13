
# Sample local.settings.json: 

```json

{
  "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "DefaultEndpointsProtocol=https;AccountName=taskqueueratelib711;AccountKey=abcdefg5H5mFscAl2mr/Utb+9K+mTBlfI7karxMOK+0Lh15OTjdGDRsHX+secretpassyoudontknow/Lw==;EndpointSuffix=core.windows.net",
    "FUNCTIONS_WORKER_RUNTIME": "java",
    "StorageToIndexer_SERVICEBUS" : "Endpoint=sb://storagetoindexer.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=secretKeyYouDontwant2bwKKk="
  }
}


```

## Instructions: 

### Prerequisites 
- JDK 
- [Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local) 
- [.NET Core 2 SDK](https://dotnet.microsoft.com/download) - (TODO: Figure out why this is needed even though we're using Extension Bundles)

## Instructions 

Add a `local.settings.json` next to host.json and run : 

`mvn clean package`
& 
`mvn azure-functions:run`

*You'll need to run `mvn clean package` before every local run or deployment*  

If you want to deploy you'll need to edit the Azure Function Deployment configuration in the `pom.xml`

```xml
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
        <azure.functions.maven.plugin.version>1.3.3</azure.functions.maven.plugin.version>
        <azure.functions.java.library.version>1.3.0</azure.functions.java.library.version>
        <functionAppName>ChangeMeToAAppFunctionAppName</functionAppName>
        <functionAppRegion>westus</functionAppRegion>
        <stagingDirectory>${project.build.directory}/azure-functions/${functionAppName}</stagingDirectory>
        <functionResourceGroup>ChangeMeToAResourceGroupName</functionResourceGroup>
    </properties>
```