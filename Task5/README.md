#   Trigger Lambda by S3

-   ![alt](./images/triger-lambda%20by%20s3.PNG)

-   Lambda function
    -   create
    -   use a blueprint
    -   blueprint name => Get S3 object
    -   function name => s3-trigger
    -   execution role =>
        -   create a new role with basic lambda permissions
-    Got to S3 and create bucket
    -   name => lamda-bucket
    -   create
-   -   go to lambda and select bucket
    -   Events types
        -   All object create events
    -   will create code
    -   ![alt](./images/code%20lambda%20fun.PNG)
-   configration of lambda fun 
    -   add permission of s3
        -   attach polices
        -   search Amazon s3 readonly access
        -   add permission

-   ![alt](./images/s3-trigger.PNG)

-   Add email that file sucessfulyy uploaded
    -   click add distnation from lambda fun trigger
        -   condtion => on success
        -   select topic
        -   save

-   -   ![alt](./images/connect%20s3%20with%20sns.PNG)

-   1-upload file  s3 bucket

-   ![alt](./images/upload%20file%20to%20s3.PNG)

-   2-will send email and logs

-   -   ![alt](./images/send%20email.PNG)
