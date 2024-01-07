
# Quickstart with CockroachDB


- Create a CockroachDB Serverless cluster
- Create a SQL user
- Connect to the cluster
- Configure the connection environment variable
- Run the Node.js sample code



This lab shows you how to use the `CockroachDB Cloud Console` to create a CockroachDB Serverless cluster and then
insert and read some sample data from a Java or Node.js sample
application.

## Create a CockroachDB Serverless cluster

Note: Organizations without billing information on file can only create one
CockroachDB Serverless cluster.


1.  If you haven\'t already, sign up for a CockroachDB Cloud account.

2.  `Log in` to your CockroachDB Cloud account.

3.  On the **Clusters** page, click **Create Cluster**.

4.  On the **Create your cluster** page, select **Serverless**.

5.  Click **Create cluster**.

Your cluster will be created in a few seconds and the **Create SQL user** dialog will display.

## Create a SQL user

The **Create SQL user** dialog allows you to create a new SQL user and
password.

1.  Enter a username in the **SQL user** field or use the one provided
    by default.

2.  Click **Generate & save password**.

3.  Copy the generated password and save it in a secure location.

4.  Click **Next**.

    Currently, all new SQL users are created with admin privileges.


## Connect to the cluster

Select a language to connect a sample application to your cluster.


Once you create a SQL user, the **Connect to cluster** dialog will show
information about how to connect to your cluster.

1.  Select **General connection string** from the **Select option**
    dropdown.

2.  Open the **General connection string** section, then copy the
    connection string provided and save it in a secure location.

    This Quickstart uses default certificates, so you can skip the
    Download CA Cert instructions.

    
    
    Note:
    

    The connection string is pre-populated with your username, password,
    cluster name, and other details. Your password, in particular, will
    be provided *only* once. Save it in a secure place (Cockroach Labs
    recommends a password manager) to connect to your cluster in the
    future. If you forget your password, a Cluster Administrator can
    reset it.
    

## Configure the connection environment variable



In a terminal set the `DATABASE_URL` environment variable to the
connection string:


```
export DATABASE_URL="<connection-string>"
```


The code sample uses the connection string stored in the environment
variable `DATABASE_URL` to connect to your cluster.



## Run the Node.js sample code

1.  Clone the `quickstart-code-samples` repo:

    
    ```
    git clone https://github.com/fenago/quickstart-code-samples
    ```
    

2.  Navigate to the `node` directory of the repo:

    
    ```
    cd quickstart-code-samples/node
    ```
    

    The code sample in this directory does the following:

    1.  Connects to CockroachDB Cloud with the `node-postgres driver` using the connection string
        set in the `DATABASE_URL` environment variable.
    2.  Creates a table.
    3.  Inserts some data into the table.
    4.  Reads the inserted data.
    5.  Prints the data to the terminal.

3.  Install the app requirements:

    
    ```
    npm install
    ```
    

4.  Run the app:

    
    ```
    node app.js
    ```
    

    The output will look like this:

    
    ```
    Hello world!
    ```
    

## Delete cluster


Warning: Deleting a cluster will delete all cluster data.


Note: Free CockroachDB Serverless clusters are subject to deletion after 6
months of no activity.


Proceed with the following steps only if you are sure you want to delete
a cluster:

1.  Navigate to the **Overview** page for the cluster you want to
    delete.
2.  Click the **Actions** button in the top right corner.
3.  Select **Delete cluster**.
4.  In the confirmation window, enter the name of the cluster.
5.  Click **Delete**.
