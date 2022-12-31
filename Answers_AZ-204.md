# **Respuestas Examen AZ-204**
## **Topic 1- Question Set 1**
1. Need to move VM1 Fromt Hyper-V host to another
    - C. **From the redeploy blade, clic Redeploy**
2. In ARM, reference an administrative password
    - **An Azure Key Vault**
    - **An Access Policy**
3. Deploy YAML manifest file
    - `kubectl apply -f myapp.yaml` (**Yes**)
4. **No**
5. **WebJobs**
    - Or Functions?
6. **Max Value** (1,2 or 3)
7. PlatformUpdateDomainCount = **20**
8. **Consumption plan** & **SendGrid binding**
9. **mongorestore** how to a strategy to migrate MongoDB to the Azure Cosmos DB account
10. Enable Managed Service Identity (MSI)
11. No change required
12. Responses:
    - B. EnablePurgeProtection
    - D. EnableSoftDelete
13. Assignments:
    1.  Users and groups
    2.  Cloud apps

    Access controls:  
    1.  Grant
14. Active Directory integrated authentication
15. B. Run the az keyvault update --enable-soft-delete true --enable-purge-protection true CLI
16. Responses:
    - avg Percentage CPU
    - window-size
17. **No** , for "store data in a geographic location that is nearest to the user"
18. **Yes**
19. **No**
20. Switch to the Standard App Service tier plan (tier D1 is a shared plan)
21. The Metric signal type
22. **Configure the QueryType property of the SearchParameters class** to allow customers to search the index by using regular expressions.
23. Logic App Code View
24. **No**. Se debe configurar Basic Gateway Credentials or Client Cert Gateway for the HTTP(s) endpoint
25. **Yes**
26. **Yes**
27. **No**
28. D. Configure the Filter property of the SearchParameters class
29. D. The Logic Apps Designer
30. OUT OF SCOPE FOR AZ-204
31. D. Add a subject prefix to sign-out events. Create an Azure Event Grid subscription. Configure the subscription to use the subjectBeginsWith filter.
32. Answer:
    - function.json:
    ```json
        "type":"http"
    ```
    - host.json:
    ```json
        "customHandler":{
            "description":{
                "defaultExecutablePath":"process.exe" //Respueta 1
            },
            "enableForwardingHttpRequest":true
        }
    ```
## **Topic 2 - Question Set 2**
1. Answer:
    - Number of VM instances: 4
    - Pricing tier: Isolated
2. Answer:
   - Azure Function Code : **Deployment**
   - Polling interval : **ScaledObject**
   - Azure Storage connection string : **Secret**
3. Answer:
   - `az appservice plan create`
   - `az webapp create / --plan $webappname`
   - `az webapp deployment / --repo-url $gitrepo --branch master --manual-integration` 
4. **No**. (No funciona activar el procesador de fotos desde eventos de Blob storage)
5. **Yes**. Update the `web.config` to include the `applicationInitialization` configuration element. Specifiy custom initialization actions to run the scripts.
6. **No**
7. **No**
8. **No**
9. For validate the client certificate in the web app. Answers:
   - Client certificate location: HTTP request header
   - Encoding type: Base64
10. Answers:
    - `az group create`
    - `az appservice plan create`
    - `az webapp create`
11. Answers:
    - `/bin/bash`
    - `az webapp create`
    - `az webapp config container set`
    - `az webapp config hostname add`
12. Answers:
    - Create the Azure Functions app with a Premium plan type
    - Create a system-assigned managed identity for the application
    - Create an access policy in Azure Key Vault for the application identity
13. D. Deploy the website to an App Service that uses the Standard service tier. Configure the App Service plan to automatically scale when the CPU load is high.
14. Answers:
    - `group`
    - `appservice plan`
    - `webapp`
    - `webapp deployment slot`
    - `webapp deployment source`
15. Answers:
    - `getContext().getRequest();`
    - `if(!("tip" in i)){`
    - `r.setBody(i);`
16. **Yes**
17. **Yes**
18. **No**
19. **Yes**
20. B. Enable the change feed on the storage account and process all changes for available events
21. Answers:
    - `FROM microsoft/aspnetcore:latest`
    - `WORKDIR /apps/ContosoApp`
    - `COPY ./ .`
    - `RUN powershell ./setupScript.ps1`
    - `CMD ["dotnet", "ContosoApp.dll"]`
22. D. Use an App Service plan. Configure the Function App to use an Azure Blob Storage trigger
23. Answers:
    - `copyIndex`
    - `copy`
    - `dependsOn`
24. Answers:
    - No
    - Yes
    - Yes
    - Yes
25. Answers:
    1. Return the most recent patient status : `Strong`
    2. Return health monitoring data that is no less than one version behind : `Bounded Staleness`
    3. After patient is discharged and all charges are assessed, retrieve the correct billing data with the final charges : `Eventual`
26. Answers:
    1.  Generalize the VM : Azure PowerShell
    2.  Store images : Azure Blob Storage 
27. Answers:
    - Add a PreBuild target in the websites csproj project file that runs the static content generation script
    - Create a file named .deployment in the root of the repository that calls a script which generate the static content and deploys the website
28. Order:
    1.  Export a Resource Manager template
    2.  Create a new template deployment
    3.  Modify the template by changing the storage account name and region
    4.  Deploy the template to create a new storage account in the target region
    5.  Use AZCopy to copy the data to the new storage account
29. Answers:
    1.  Firewall configuration: Run Command
    2.  Supporting services script: Customer Script Extension
30. Answers:
    - `New-AzResourceGroup`
    - `New-AzAppServicePlan`
    - `New-AzWebApp`
    - `New-AzWebAppSlot`
31. Answers:
    - `IdentityId` #Should be IdentityType
    - `$SystemAssigned`
32. **No**
33. **Yes**
34. Answers:
    - A log alert is created that sends an email when the CPU percentage is above 60 percent for five minutes: **No**
    - A log alert is created that sends an email when the number of virtual machine heartbeats in the past hour is less than five: **Yes**
    - The log alert is scheduled to run every two hours: **No**
35. Answers:
    - Enable developers to write the functions by using the Rust language: `Custom handler`
    - Declaratively connect to an Azure Blob Storage account: `Extension bundle`
36. Answers:
    - `WEBSITES_ENABLE_APP_SERVICE_STORAGE`
    - `/home`
37. Answers:
    - A. In the Azure Application Gateway´s HTTP setting, enable the Use for App service setting
    - D. In the Azure Application Gateway´s HTTP setting, set the value of the Override bakend path option to contoso22.azurewebistes.net
38. **No**
39. A. Add the customer ID for the signed in user to the CorrelationContext in the web application
40. Answers:
    - Publish: `Code`
    - Runtime stack: `Custom Handler`
    - Version: `custom`
41. Answers:
    1. `dism /image:\ /get-packages > c:\temp\Patch.txt`
    2. Open `C:\temp\Pacht.txt` file and locate the update that is in a pending state
    3. `dism /Image:<Attached OS diks>:\ \Remove Package /PackageName:<package name to delete>`
    4. Detach the OS disk and recreate the VM
42. **No**
43. Answers:
    1. `context.SetOutput(input[errIndex])`
    2. `Completed`
    3. `output`
44. Answers:
    -  A. Orchestrator
    -  D. Activity
45. Answers:
    - Determine whether the templates follow recommended practices: `Azure Resource Manager test toolkit`
    - Test and validate changes that templates will make to the environment: `What-if operation`
## **Topic 3 - Question Set 3**
1. Answers:
    - The code creates an infinite lease: Yes
    - The code at line 06 always creates a new blob: No
    - The finally block releases the lease: Yes
2. B. between one and 15 hours
3. Answers:
    - `consistencyLevel = BoundedStaleness`
    - `--enable-automatic-failover true \`
    - `--locations 'southcentralus=0 eastus=1 westus=2'`
4. Answers:
    - `sku B1 --is-linux`
    - `--deployment-container-image-name images.azurecr.io/website:v1.0.0`
    - `container set --docker-registry-server-url https://images.azurecr.io -u admin -p admin`
5. Answers:
    1. Service Bus queue
    2. Active Message Count
    3. Average
    4. Less than or equal to
    5. Decrease count by
6. Answers:
   - FetchAttributesAsync
   - Metadata.Add
   - SetMetadataAsync
7. **No** (Instead should be Event Hub)
8. QueueClient
9. Actions:
   1. Upgrade the storage account to GPv2
   2. Create a new GPv2 Standar account and set its default access tier level to cool
   3. Copy the data to be archived to a Standard GPv2 storage account and then delete the data from the original storage account
10. new CosmosClient(EndpointUri, PrimaryKey);
11. AzCopy
12. Answers:
    1.  Segment1: `http://169.254.169.254/metadata/identity/oauth2/token`
    2.  Segment2: `JsonConvert.DeserializeObject<Dictionary<string,string>>`
13. Answers:
    1.  `compositeIndexes`
    2.  `descending`
14. Answers:
    - Number of partitions: 6
    - Partition Key: Highway
15. Answers:
    1.  Deploy solution: `Helm`
    2.  View cluster and external IP addressing: `Kubectl`
    3.  Implement a single, public IP endpoint that is routed to multiple microservices: `Ingress Controller`
16. Answers:
    1.  FutureOrders: No Filter
    2.  HighPriorityOrders: Correlation Filter
    3.  InternationalOrders: SQL Filter
    4.  HighQuantityOrders: SQL Filter
    5.  AllOrders: SQL Filter
17. Answers:
    1.  A user request the image from the CDN URL. The DNS routes the request to the best performing POP location.
    2.  If no edge servers in the POP have the image in cache, the POP requests the file from the origin server
    3.  The origin server returns the logo image to an edge server in the POP. An edge server in the POP caches the logo image and returns the image to the client.
    4.  Subsequent request for the file may be directed to the same POP using the CDN logo image URL. The POP edge server returns the file from cache if the TTL has not expired
18. Answers:
    1.  D. a concatenation of multiple property values with a random suffix appended
    2.  E. a hash suffix appended to a property value.
19. Answers:
    1.  Yes
    2.  Yes
    3.  Yes
20. Answers:
    1.  Store the data from which the change feed is generated: Monitored container
    2.  Coordinate processing of the change feed across multiple workers: Lease container
    3.  Use the change feed processor to listen for changes: Host
    4.  Handle each batch of changes: Delegate
21. Answers:
    1.  Configure an Azure Storage account: implement StorageV2
    2.  Configure data retention: Set a lifecycle management policy to move blobs to the cool tier
22. Answers:
    1.  SaveScore will work with Cosmos DB: Yes
    2.  SaveScore will update and replace a record if one already exists with the same playerId and gameId: No
    3.  Leader board data for the game will be automatically partitioned using gameId: No
    4.  SaveScore will store the values for the gameId and playerId parameters in the database: Yes
23. A. Export the Azure Storage acoount Azure Resource Manager template
24. Answers:
    1.  Azure Cosmos DB API: `Core (SQL)`
    2.  Azure Cosmos DB partition key: `item id`
25. Answers:
    1.  Monitor the progress of the change feed processor: `Change feed estimator`
    2.  Prevent the change feed processor from retrying the entire batch when one document cannot be read: `Dead-letter queue`
26. Answers:
    1.  Block blobs prefixed with transactions will transition blobs that have not been modified in over 60 days to cool storage, and delete blobs not modified in 365 days: **No**
    2.  Blobs are moved to cool storage if they have not been accessed for 60 days: **No**
    3.  The policy rule tiers previous version within a container named transactions that are 60 days or older to the cool tier and deletes previous version that are 365 days or older: **Yes**
    4.  Blobs will automatically be tiered from cool back to hot if accessed again after being tiered to cool: **No**
27. D. Set the indexing mode to Consistent
28. Answers:
    1.  C. Update the ConnectionPolicy class for the Cosmos client and set the UseMultipleWriteLocations property to true
    2.  D. Create and deploy a custom conflict resolution policy
29. Answers:
    1.  Search and filter by customer identifier: **Azure Blob index tags**
    2.  Search information inside documents: **Azure Cognitive Search**
30. Answers:
    1.  HTTP Header value: `ETag`
    2.  Conditional header: `If-Match`
31. Answers:
    1.  `DeleteSanpshotsOption`
    2.  `OnlySnapshots`
32. Answers:
    1.  `delete_snapshots`
    2.  `Only`
## **Topics 4 - Question Set 4**
1. C. Cosmos DB Operator
2. No
3. Yes
4. No
5. Answers:
   1. Enable retention period and accidental deletion: `Soft delete`
   2. Enforce retention period and accidental deletion: `Purge protection`
6. Answers:
   - A. Basic Authentication
   - D. OAuth Client Credential Grant
7. Answers:
   1. Permission: user_impersonation
   2. Type: delegated
8. Answers:
   1. UseAuthentication
   2. UseAuthorization
   3. UseAzureAppConfiguration
9. A. Create a single user-assigned Managed Identity with permission to access Key Vault and configure each App Service to use that Managed Identity
10. Yes
11. No
12. No
13. Answers:
    1.  keyvault
    2.  keyvault key
    3.  vm 
    4.  vm encryption
    5.  all
14. C. Managed identity
15. Answers:
    1.  `Get-AzSubscription`
    2.  `Set-AzContext`
    3.  `Get-AzStorageAccountKey`
    4.  `$secretvalue = ...`
    5.  `Get-AzKeyVaultSecret`
16. No
17. No
18. Answers:
    1.  DeliveryRuleDeviceConditionParameters 
    2.  Mobile
    3.  DeliveryRequestHeaderConditionParameters
    4.  HTTP_USER_AGENT 
    5.  iPhone
19. No
20. Yes
21. Answers:
    1.  "groupMembershipClaims"
    2.  "ouath2AllowImplicitFlow"
22. B. Create an Event Grid topic that uses the Start-AzureStorageBlobCopy cmdlet
23. A. single path
24. C. Managed identity
25. D. validate-jwt
26. Answers:
    1.  Set-variable:Inbound
    2.  Cacke-lookup-value:Inbound
    3.  Cache-store-value:Inbound
    4.  Find-and-replace:Outbound
27. Answers:
    1.  SecretClient
    2.  DefaultAzureCredential
28. Answers:
    1.  A. Microsoft Graph API
    2.  B. Microsoft Authentication Library (MSAL)
29. Answers:
    1.  A. Revoke the delegation key
    2.  D. Remove the role assignment for the security principle
30. Answers:
    1.  Generate a Key Exchange Key (KEK)
    2.  Retrieve the Key Exchange Key (KEK) public key
    3.  Generate a key transfer blob file by using the HSM vendor-provided tool
    4.  Run the `az keyvault key import` command
31. A. Create a user-assigned managed identity and assign role-based access controls