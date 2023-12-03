# Connect NLB with two instances
# Connect ALB with two Instances
# Connect NLB with ALB

-   ![alt](./images/loadblancer.PNG)

## Ans:

-   1- Create VPC  fast way => VPC and more(will create vpc and  subnet and route table)
    -   CIDR => 10.0.0.0/16
    -   choose number of subnet 2 public and 2 private
    -   Edit subnet settings =>  auto assign public ip
-   1-install web server in ec2
    -   create ec2
        -   name => web1
        -   select keypair
        -   select vpc and subnet
        -   create secuirty group => add role open port 80 http  source anywere 0.0.0.0/0
        - advanced details and insert code in user data to install httpd
        -   run shell script in boot of instance

        ```bash

        #!/bin/bash
        # Use this for your user data (script from top to bottom)
        # install httpd (Linux 2 version)
        yum update -y
        yum install -y httpd
        systemctl start httpd
        systemctl enable httpd
        echo "<h1>Hello World my name is mostafa hussien from $(hostname -f)</h1>" > /var/www/html/index.html

        
        ```

        -   Launch Instance
    2-install web2 server in ec2 in the same pervious way but in another subnet


    -   3-create Loadblancer  [Application Load blancer]
        -   name => alb
        -   scheme => Internet facing
        -   select vpc
        -   mapping trafic in all avalibilty zone
        -   create secuirty group and select it
            -   name => lb-sg
            -   select vpc
            -   add rule => open port http
        -   Listner and routing 
            -   traffic port 80 will send to "target group"(connect load balncer with instance)
            -   creat target group  and select
                -   type => instances
                -   name => alb-tg
                -   select vpc
                -   next and register target
                -   select instances and include as pending below
                -   creat target group
        -   creat load balncer

    -   copy dns record of load blancer and run in browser
    -   will route traffic between this two instances
    -   ![alt](./images/application%20loadbalancer.PNG)

-   create Network load balncer 
    -   name => nlb
    -   scheme => internet facing
    -   select vpc
    -   mapping trafic in all avalibilty zone
    -   select secuirty group
    -   create target group  and select
        -   type => instances
        -   name => nlb-tg
        -   select vpc
        -   next and register targets
        -   create target group
    -   create load balncer
-   copy dns record of load blancer and run in browser
-   will route traffic between this two instances
-   ![alt](./images/network%20loadblancer.PNG)




            







