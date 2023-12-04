#   ECS Cluster - Service 4 Tasks
#   Connected with Application Loadbalancer

-   ![alt](./images/ECS%20Cluster.PNG)

-   Search ECS
-   Create Cluster
    -   name => fargate
    -   infrastructure => AWS Fargate (will create automatic asg )
    -   Create

-   1-create task defintion
    -   Create new task difintion
        -   name => ecs-td
        -   infrastructure => fargate
        -   cpu and memory
        -   container
            -   name => nginx
            -   image url => nginxdemos/hello
    -   create
-   2-go to cluster and create task
    -   deployment services => task
    -   familly or task defintion => select task defintion
    -   desire task => 2
    -   select vpc
    -   create secuirty group
        -   open port 80 http
    -   create

-   3-go to cluster and create service
    -   deployment services => service
    -   family =>select task deifintion
    -   select replica
    -   desire task => 4
    -   slect vpc and securty group open port 80
    -   loadbalancer => application
        -   name => ecs-alb      
        -   create target group
    -   create

    -   take url of load balancer and run in browser

-   ![alt](./images/Four-services%20running.PNG)

-   ![alt](./images/ECS-Application%20Load-Balancer.PNG)