# AWS S3 HACKERONE REPORT
  
# VULNERABILITY NAME: 
Listing of Amazon S3 Bucket accessible to any amazon authenticated user (vector-maps-e457472599)

# SUMMARY:
It's possible to get a listing of every files in the S3 bucket vector-maps-e457472599

# DESCRIPTION: 
The problem is using the AWS command line, it's possible to get a listing of files in the Amazon S3 Bucket with an AWS authentication. See screenshot vector-maps-e457472599_public_s3_bucket.png
This user authentication is easy to get and it's free from Amazon.
The good news is that the ACL on the files are set the way that's impossible at moment to create any file from the bucket using my authentication. I did not test removing any file from the bucket.
A secure amazon S3 bucket would show Access Denied like your other bucket named brda-vector-maps in screenshot brda-vector-maps_access_denied_s3_bucket.png

# STEP-BY-STEP REPRODUCTION INSTRUCTIONS:
With the aws-cli tool installed and configured :
aws s3 ls s3://vector-maps-e457472599

# ATTACHED SCREENSHOTS:
SCREENSHOT 1: brda-vector-maps_access_denied_s3_bucket.png
SCREENSHOT 2: vector-maps-e457472599_public_s3_bucket.png

# IMPACT:
This give more information about your buckets to an attacker that are looking to attack you.
Also, considering that it's possible to set the wrong ACL on a file that you may upload and may be confidential in the bucket, a secure bucket will remove the possibly to access it without a proper authentication.
