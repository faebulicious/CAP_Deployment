# Step-by-Step Deployment

Each commit contains one single step

## Step 0: Create CAP app
Create new CAP app by using `cds init`. Add some cds files manually or use command `cds add sample`.

## Step 1: Add HANA Support
Add HANA support by using `cds add hana --for production`.

## Step 2: Add XSUAA Support
Add XSUAA support by using `cds add xsuaa --for production`.

## Step 3: Add MTA Feature
Create the File `mta.yaml` by using `cds add mta`. The newly created file will contain the service app, the db deployer app, the xsuaa service and the hana hdi service.

## Step 4: Create UI5 App
Create a new UI5 App (Elements of Freestyle) using the official Fiori App Generator. Make sure the option to adjust the `mta.yaml` is selected. Also make sure to configure the Fiori Launchpad (FLP) navigation.

When requested to enter the name of the destination, choose any name. You'll reuse the name of the destination later.

The `mta.yaml` file is extended by the html5 repository and the destination service. Also the necessary modules for building and packaging the UI5 app are added.

## Step 5: Adjust Destinations
In the last step, an other additional module is required to created the destinations at deployment time. Refer to the `mta.yaml` file in this commit as this is a manual step. Make sure that the name of the destination for your CAP service matches the name of the destination in the `xs-app.json` file (step 4) of your UI5 app.

Also the `manifest.json` file of your UI5 app must be extended by the property `sap.cloud`. The value has to be unique within your HTML5 repository and must also be used in the above defined destinations. 

If this property is missing the deployment will work but the app will not appear in the HTML5 Repository of your BTP.