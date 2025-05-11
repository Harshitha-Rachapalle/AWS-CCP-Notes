# AWS Organizations

* It's a global service wich allows to create multiple AWS accounts

* The main account is the master account and remaining are child accounts

* cost benifit is that **consolidated billing**: which means all the accounts bill is paid by master in a single payment

*  API is available to **automate AWS account creation**

* **Restrict account privileges using service control policies (SCP)**

## AWS Control Tower

* easy way to set up & govern a secure and complaint multi account AWS environment based on best practices

* AWS control tower runs on top of AWS organizations

## AWS Resource access manager (AWS RAM)

* We can share our resources with other aws accounts in our organization.

* the resources are interlinked and can be used in differnt accounts.

## AWS SERVICE catalog

*users need a self service portal to launch a set of authorized products predefined by admins

> As a Admin in aws & service catalog , going to create a product that are cloud formation templates
and include in a portfolio is a collection of products and define who has access to launcing what products within my portfolio- i.e IAM permissions to access portfolios
 
> When a user log into ur portal on service catalog and users can access the product list and can launch a product and automatically they get provisioned by cloud formation

## pricing models in AWS
there are 4 types

1. **Pay as you go**:  pay for what u use

2. **Save when you reserve**: to minimize risks, predicting manage budgets
 
    eg: Reservations are available for EC2 reserved instances, DuynamoDB reserved capacity,
   Elasticcache reserved nodes, RDS reserved instance, Redshift reserved nodes

 3. **Pay less by using more**: volume based discounts

 4. **Pay less as AWS grows**

