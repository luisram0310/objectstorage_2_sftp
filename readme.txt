Introduction

This is an example OCI Function to SFTP a file on a node to OCI Object Storage. The private key is specified in OCI Vault in a secret, the
secret is passed into the function along with the OS user for SFTP, the IP/hostname and the target bucket and object name.

You must create a secret with the private key for SFTP'ing to the host. Also ensure the functions resource principal can access the secret.

Example:

1. Sftp a file in to a bucket in OCI Object Storage - by default does a PUT
echo '{"sftp_file":"SOURCE_FILE_NAME", "object_name":"TARGET_OBJECT_NAME","bucket":"TARGET_BUCKET_NAME", "user":"SOURCE_OS_USER", "host":"SOURCE_IPADDRESS", "secret":"SECRET_OCID"}' | fn invoke distools disfunctionsftp
ue.
ie.
echo '{"sftp_file":"mysourcedata.csv", "object_name":"fromsftp","bucket":"disdemodatax", "user":"opc", "host":"IPADDRESS", "secret":"SECRET_OCID"}' | fn invoke distools disfunctionsftp


2. Sftp GET a file from object storage and save in SFTP server
echo '{"operation":"GET","sftp_file":"mytargetdata.csv", "object_name":"fromsftp","bucket":"disdemodatax", "user":"opc", "host":"IPADDRESS", "secret":"SECRET_OCID"}' | fn invoke distools disfunctionsftp
ie.
echo '{"operation":"GET","sftp_file":"TARGET_FILE_NAME", "object_name":"SOURCE_OBJECT_NAME","bucket":"SOURCE_BUCKET_NAME", "user":"TARGET_OS_USER", "host":"TARGET_IPADDRESS", "secret":"SECRET_OCID"}' | fn invoke distools disfunctionsftp
