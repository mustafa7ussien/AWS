# Host Static Website in S3 

-   S3
-   Create buckets
-   upload website
-   name => my portfolio
-   properties
    -   Static website hosting => enabled
    -     index document => index.html
-   permissions => un block public access
-   bucket policy 
    -   edit and policy generater
        -   choose s3 bucket policy
        -   effect => allow 
        -   princple => *
        -   action => GetObject
        -   ARN => copy from edit bucket policy
    -   Add statment
    -   copy code and insert in policy 
    -   in resource => in end => /*


-   ![alt](./images/static%20website%20with%20s3%20bucket.PNG)