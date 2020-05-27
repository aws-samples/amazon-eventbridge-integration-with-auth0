# Configure A new S3 datasource for QuickSights:
In this applicaition, you connect QuickSights to Amazon S3 and use the csv files as the data source. A manifest file named `manifest.json` has been provided for you in the GitHub repository.  Open this file and replace `{your-S3-bucket-name}` with the name of the S3 bucket that was generated when you deployed the application, then save the file.

### Granting QuickSight permission to access your S3 bucket:

1.	Choose the user profile icon in the top right of the menu bar, then choose Manage QuickSight.
2.	Choose Security & permissions, then choose Add or remove.
![S3 Permissions](https://raw.githubusercontent.com/bls20AWS/Auth0EventBridge/master/images/s3Permissions.png "S3 Permissions Dashboard")

3.	Choose the checkbox next to Amazon S3, then select the application bucket, the name contains AuthZeroToEventBridgeActivityLogs. Choose Finish. 
![S3 Buckets](https://raw.githubusercontent.com/bls20AWS/Auth0EventBridge/master/images/s3Buckets.png "S3 Permissions Dashboard")


### Create a new Data source

1.	Go to the QuickSight console and choose Manage data
1.	Choose New data set, then choose S3
1.	Enter auth0UserLogs in the Data source name field, then choose the Upload radio button.
1.	Choose the Folder Icon in the Upload a JSON manifest file field, browse to the example manifest.json file you edited earlier and choose Open, then choose Connect.
1.	Once the dataset has been created, choose Visualize.

![Configure A new S3 dataset for QuickSigts](https://raw.githubusercontent.com/bls20AWS/Auth0EventBridge/master/images/NewS3DataSource.png "Configure A new S3 dataset for QuickSigts")

