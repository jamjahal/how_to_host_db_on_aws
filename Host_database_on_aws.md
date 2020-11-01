# How to host a database on AWS

1. Create an AWS account (you can sign up for a free tier account)
2. Follow Step 1 and Step 2 of [these instructions](https://aws.amazon.com/getting-started/tutorials/create-connect-postgresql-db/) 

Set the password to something easy to remember.

Be sure to select the **Free Tier** Template, this will grey out options that can cost money.

![Free Tier](images/free_tier.png)

3. Launch PG Admin

4. In PG Admin right click on a server group (base of file tree) in the left pane, and click Create > Server

![create_server](images/create_server.png)

5. Follow [these instructions](http://127.0.0.1:53226/help/help/server_dialog.html) to name your server and set up the connection.  You can ignore the SSL, SSH Tunnel, and Advanced tabs for now.

* When setting up the connection, the host name / address can be found back in AWS by clicking on the database you created and copying the endpoint address.  It should look something like `database_name.xxxxxxxxxx.us-east-1.rds.amazonaws.com`

![click on your database](images/click_db.png)


![database endpoint](images/endpoint.png)

6. Now you can create a database and add data to this database in pgadmin and it will be saved in the cloud. 

7. To access the data from python, you will set the engine to something that will look like:

`postgresql://postgres:password@database_name.xxxxxxxxxx.us-east-1.rds.amazonaws.com:5432/your_db_name`

You will of course swap out your own password, endpoint and datbase.  To recap, the formula for the sql engine in python is 

`<database_type>://<database_user>:<password>@<host_endpoint>:<port>/<database_name>`


Now you should be able to access the data in python from the AWS server.
