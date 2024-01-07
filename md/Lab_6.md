
# Lab 6: Modifying the Terraform script to update the CockroachDB deployment

This lab shows you how to modify the Terraform script to update the CockroachDB deployment
using the CockroachDB Cloud Terraform provider.


## Before you begin

Before you start this lab, make sure you have created the cluster in Lab 3.


## Create the Terraform configuration files

Terraform uses a infrastructure-as-code approach to managing resources.
Terraform configuration files allow you to define resources
declaratively and let Terraform manage their lifecycle.


In this lab, you will update a CockroachDB Serverless cluster.

2.  In a text editor update file `terraform.tfvars` created ion lab3 with the
    following settings:

    
    ```
    cluster_name = "{cluster name}"
    sql_user_name = "{SQL user name}"
    sql_user_password = "{SQL user password}"
    ```
    

    Where:

    -   `{cluster name}` is the name of the cluster you want to create.
    -   `{SQL user name}` is the name of the SQL user you want to
        create.
    -   `{SQL user password}` is the password for the SQL user you want
        to create.

    For example, the following `terraform.tfvars` file creates a
    CockroachDB Serverless with a `maxroach2` SQL user.

    
    ```
    cluster_name = "blue-dog"
    sql_user_name = "maxroach2"
    sql_user_password = "Fenago@12345"
    ```
    

3.  Create an environment variable named `COCKROACH_API_KEY`. Copy the `API key` created in Lab 3.

    
    ```
    export COCKROACH_API_KEY={API key}
    ```
    

    Where `{API key}` is the API key you copied from the CockroachDB Cloud Console.



## Update the cluster


2.  Create the Terraform plan. This shows the actions the provider will
    take, but won\'t perform them:

    
    ```
    terraform plan
    ```
    

3.  Update the cluster:

    
    ```
    terraform apply
    ```
    

    Enter `yes` when prompted to apply the plan and create the cluster.


## Get information about your cluster

The `terraform show` command shows detailed information of your cluster
resources.


```
terraform show
```


This will show the following output:


```
# cockroach_cluster.example:
resource "cockroach_cluster" "example" {
    cloud_provider    = "GCP"
    cockroach_version = "v22.1"
    creator_id        = "98e75f0a-072b-44dc-95d2-cc36cd425cab"
    id                = "1aaae1f8-19e2-4653-ba62-db16de2a84b9"
    name              = "blue-dog"
    operation_status  = "CLUSTER_STATUS_UNSPECIFIED"
    plan              = "SERVERLESS"
    regions           = [
        # (1 unchanged element hidden)
    ]
    serverless        = {
        routing_id  = "blue-dog-6821"
        spend_limit = 0
    }
    state             = "CREATED"
}

# cockroach_sql_user.example:
resource "cockroach_sql_user" "example" {
    cluster_id = "1aaae1f8-19e2-4653-ba62-db16de2a84b9"
    id         = "1aaae1f8-19e2-4653-ba62-db16de2a84b9:maxroach"
    name       = "maxroach2"
    password   = (sensitive value)
}
```



**Note:** You can delete the cluster by running `terraform destroy` command but you will be using cluster in upcoming labs so don't delete it yet.



### Task: Update the Cluster Name

Update **cluster_name** in `terraform.tfvars` and run the above terraform commands.


