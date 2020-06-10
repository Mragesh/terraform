# terraform

## Create a service principal (account to control Kubernetes cluster)
1) Azure Active Directory -> Create a tenant
2) Azure Active Directory -> Register application -> Create New Application
3) Get Application/Client ID
	b78692cb-0d67-417e-a8e3-f96a35c94082
4) Get Tenant/Directory ID
	9065b0df-7267-4ed6-aa7f-8d5d99dae2d9
5) Azure Active Directory -> Register application -> Certificates & secrets -> New client secret
	~NAdAZ9-~ansrI4RIhmEN_FIj7s3RDUn_A

## Give service principal access to AKS
6) All Services -> Subscription -> Change directory (to tenant created in step 1)
7) All Services -> Subscription -> Get subscription ID to be associated to service principal
   c1328f4d-8db6-4749-918c-418a2b978e5f
8) Subscriptions -> Access Control (IAM) -> Add Role Assignment
	Role -> Contributor (will be able to access everything running on AKS except providing access to others)
	Assign Access to -> Azure AD user, group or Service Principal
	Select -> Service Principal (Created in step 2)

## Create Cluster

9) Ensure that the service works 
	az login --service-principal -u b78692cb-0d67-417e-a8e3-f96a35c94082 -p ~NAdAZ9-~ansrI4RIhmEN_FIj7s3RDUn_A --tenant 9065b0df-7267-4ed6-aa7f-8d5d99dae2d9
