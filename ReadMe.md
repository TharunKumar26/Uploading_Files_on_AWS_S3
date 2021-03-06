
## Uploading Files to AWS server with Node Js and Python

### On Client Side

```
<div>
<form onsubmit="/submit" method="POST">
<input type="file" id="file" onchange="uploadfile(e)">
<input type='submit'>
</form>
</div>

<script>

function upload file(e){
formdata = new Formdata()
var file_upload = event.target.files[0]
if(!file){
alert('No file was selected!!')
}
}
</script>
```

## Implementation on Server Side




  After Creating an S3 Bucket in AWS, We can read/write.

Getting Secret Credentials ,
```
1. AWS_ACCESS_KEY_ID

2. AWS_SECRET_ACCESS_KEY

3. Bucket name

4. Region
```

  
  ### JavaScript :

we can use AWS-SDK plugin to read/write data to S3 Bucket
```
npm install aws-sdk
``` 
Then, Importing the necessary libraries
```
const fs = require('fs'); 
const AWS = require('aws-sdk');
```
Now, we can perform uploading files with the code below
```
const fileContent = fs.readFileSync(fileName); 
// Setting up S3 upload parameters  
const params = { Bucket: BUCKET_NAME, Key: filename, Body: fileContent }; 
// File name to save as in S3 
// Uploading files to the bucket 
s3.upload(params, function(err, data) { 
	if (err) { throw err; } 
	console.log(`File uploaded successfully. ${data.Location}`); 
	});
```
If the operation is success then we can see the output as 
```
"File uploaded successfully {Bucket address}"
``` 
  ### Python :
The boto3 library helps to interact with AWS S3 bucket in Python
```
pip install boto3
```
On the Server Side, With the help of boto3, we can initialize the S3 bucket client
  ```
import boto3

client = boto3.client('s3', region_name='Region_name')
try :
	client.upload_file('"filepath"+'filename' ', 'mybucket', 'filename_to_be_saved')
except ClientError as e:
	logging.error(e)
```
See Full documentation on Uplaoding Files with Boto3 https://boto3.amazonaws.com/v1/documentation/api/latest/guide/s3-uploading-files.html

This is the basic code to upload a file to AWS S3 bucket.






