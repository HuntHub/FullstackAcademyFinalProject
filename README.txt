----------SCRUM EATS READ ME----------


****Please note that this app is undergoing constant change, info many not always be 100% accurate. Contact Scrum Eats for help****


--Please use a search function quickly locate your desired notes section.




    TABLE OF CONTENTS:

        dynamodb_handler notes
        app.py notes
        terraform notes




-----dynamodb_handler.py notes-----


-YOU MUST DO THIS IN ORDER FOR THE APP TO BE ABLE TO COMMUNICATE WITH AWS.

-Find your AWS credentials and paste them in the correct variable slots at the top of dynamodb_handler.py file.
  Be sure to maintain quotation marks around each line of credentials.

  *Config file dedicated to patching in credentials to come soon.*


----end dynamodb_handler notes----


-----app.py notes-----


-NOTE: First-time users may have to manually enter data into their table.
        This app does not currently support the full provisioning of a table with data in it from scratch.
        Please use our associated Terraform file or the desired equivalent.
        However, this app will create a table named "Food" if one does not already exist.


-Use the syntax below when making requests to the DB.


    {
    "food" : "<food>",
    "id"   :  <id>,
    "likes":  <likes>,
    "price": "<price>",
    "truck": "<truck>",
    "type": "<type>"
    }  


-Make sure you are using the correct path for each request type.

    Example:

    The line below is the function that adds an item.

        @app.route('/food', methods=['POST'])

    Go to the location that the app is running on (typically: http://localhost:5000).
    And then add the '/food' (remove single quotes) from the app route line to the end of the address.

    Then make sure you are using the correct function associated with that address.
    In this case we are making a 'POST' request as stated in the methods=['POST'] portion of the line.

    As long as your syntax is correct and you are making the correct type of request to the correct address, your item will post
    and you should see a message saying that your request was successful.

    If you do not see that message, double check your syntax, request type, and address.

    If problem persists, contact Scrum Eats support for help.


----end app.py notes----


-----terraform notes-----

-The Terraform files contained in this repository must be copied in their entirety in order for them to function properly.
 The files will form an entire environment from scratch in your AWS account.
 
 REMEMBER YOU MUST AUTHENTICATE YOUR ACCESS BY ENSURING THE PROPER CREDENTIALS ARE IN YOUR /aws/credentials FILE
 
    File list:
        compute
        database
        key
        main
        network
        notification
        output
        policies
        providers
        variables
        
     
     
--compute
    The compute file stores the configuration information for our EC2 instances including our app server, bastion host, and monitoring instance.
    
    -App server
        
        The main location where the application itself resides within our ecosystem.
        The instance is programmed to initialize and then, through a series of automated user inputs, install our app along with necessary dependencies.
        
    -Bastion host
        
        The bastion host is dedicated to thwart incoming attacks.
        
    -Monitoring server
    
        The monitoring server is dedicated to providing in-depth monitoring information to external resources and endpoints.
        
        
--database
    The database file stores the configuration information for our database.
    *File under development to work in conjunction with the app's inherent function to create a table within DynamoDB*
    
    
--key
    The key file generates and allocates key pairs for our instances and downloads the private key to the directory that is running Terraform.
    This allows for easy SSH ability when used in conjunction with the IP addresses declared in the output.
    
    
--main
    This file creates our VPC
    
    
--network
    This file addresses all things networking related including internet gateways, route tables, subnets, elastic IPs, and network interface cards.


--notification
    This file contains the configuration information for SNS to notify customers.
    
    
--output
    This file gathers various essential pieces of information and shows them to the user upon a successful terraform apply. Can also be called with terraform show.
    
    
--policies
    This file creates various policies that allow access to and from resources.


--providers
    This file provides essential configuration information for Terraform
    
    
--variables
    This file contains variables that can be called from any Terraform file.
        
    
----end terraform notes----
