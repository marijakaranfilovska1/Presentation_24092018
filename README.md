This web API doesn’t have any valuable code. It is created in order to work with Web App Service in Azure.
#	Create App Service Plan. 
It should not have basic pricing tire. Basic pricing tire does not give you chance to work with deployment slots.
#	Create Web App as part of that App Service Plan. 
Create new resource group for that Web App.
#	Deploy web API to Web App on Azure
##	Deploy it from visual studio 
Right clock on the project -> Publish -> New Profile -> Select Existing -> Publish -> select the resource group -> select Web App -> OK
## Deploy it from a source (e.g. GitHub)
###	GitHub
•	Create new project there
•	project from GitHub connect with your web API in the Visual Studio. Push your code on GitHub.
### Azure portal 
• open your Web App -> Deployment options -> Choose source -> GitHub -> Authorization -> Choose project from GitHub -> Choose branch (you should choose the branch from which it will deploy directly to this Web App (deployment slot)) -> OK
•	After this steps deployment on Azure portal will go automatically.
•	You can redeploy 
open your Web App -> Deployment Center (Preview) -> choose the deployment which you want to redeploy
#	Deployment Slots
##	Create deployment slot
•	open your Web App -> Deployment slots -> Add slot -> add the name of the slot -> choose do you like to clone configuration from existing slot -> OK
##	Zero downtime deployment -  Swap deployment slots
•	open your Web App -> Deployment slots -> Swap -> choose swap type -> choose which deployment slots will be swapped
•	Swap – means swapping virtual IP
it swaps:
	General settings (.net framework version, Web Sockets)
	Connection strings
	Handler Mappings
	Application and site diagnostic settings
	Monitoring settings

it doesn’t swap
	Publishing endpoints
	Custom Domain Names
	SSL certificates and bindings
	Scale settings

• You can revert deployment if you swap back deployment slots
• Deployment Custom - Kudu
## Testing in production
• open your Web App -> Testing in production -> choose deployment sot on which you will redirect % of your traffic
#	Scaling up/out
•	Scaling up means using more resources
•	Scaling out means using more instances of your app.
#	Authentication / Authorization
•	Authentication access can be enabled just on the main App Service
•	open your Web App -> Authentication / Authorization -> set it to “ON” -> choose Authentication providers -> configure it
•	You can add users from Microsoft to have access to the Web app
open your Web App -> Access control (IAM) -> Add -> choose role -> choose assigne access to -> select the user
#	Custom domains
##	Add domain and SSL (security socket layer) certificate
• open your Web App -> Custom domains -> Add hostname -> enter Hostname (if your are using Traffic manager, than here you should add it’s IP address)
## Add (security socket layer) certificate	
• open your Web App -> SSL settings -> Private certificate -> import/upload
•	open your Web App -> SSL settings -> Bindings -> add SSL Bindings
#	Traffic management
Azure provides more load-balancing solutions:
• Load Balancer
• Application gateway
• Traffic manager
