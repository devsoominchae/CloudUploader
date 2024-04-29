# CloudUploader
Uploads local file to AWS S3 bucket

# Usage
1. Install aws in CLI
```bash
sudo apt-get install aws-cli
```
2. Configure credentials
```bash
aws configure
```
3. Clone repository
```bash
git clone https://github.com/devsoominchae/CloudUploader.git
```
4. Give execution permissons to the script
```bash
cd CloudUploader && chmod +x clouduploader
```
5. Add the following line to `~/.bashrc`
```bash
export PATH="$PATH:/path/to/CloudUploader"
```
and run
```bash
source ~/.bashrc
```
6. Run clouduploader
```bash
clouduploader /path/to/upload bucket_name
```

### Example Output
`--url` option at the end will print the sharable URL
```bash
$ clouduploader /path/to/test.txt /path/to/output_file.txt /path/to/test bucket-name --url
upload: ../test.txt to s3://bucket-name/test.txt                  
Upload successful
URL : https://bucket-name.s3.amazonaws.com/test.txt

upload: ../output_file.txt to s3://bucket-name/output_file.txt
Upload successful
URL : https://bucket-name.s3.amazonaws.com/output_file.txt

upload: ../test to s3://bucket-name/test
Upload successful
URL : https://bucket-name.s3.amazonaws.com/test
```

```bash
clouduploader /path/to/test bucket-name
File /path/to/test exists in bucket-name. Would you like to skip(s), rename(r), overwrite(o)? s
Skipping upload /path/to/test
```

```bash
clouduploader /path/to/test bucket-name
File /path/to/test exists in bucket-name. Would you like to skip(s), rename(r), overwrite(o)? r
Enter new name for the /path/to/test : test_new
/path/to/test will be uploaded as test_new
upload: ../../../tmp/test_new to s3://bucket-name/test_new
Upload successful
```

```bash
clouduploader /path/to/test bucket-name
File /path/to/test exists in bucket-name. Would you like to skip(s), rename(r), overwrite(o)? o
/path/to/test will be copied to bucket-name
upload: ../test to s3://bucket-name/test
Upload successful
```
