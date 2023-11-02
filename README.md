# Run Microservices on local/dev machine
This repo will demonstrate how to run and debug frontend and backend event driven microservices on local/Dev machine with [Tye](https://github.com/dotnet/tye/blob/main/docs/tutorials/hello-tye/00_run_locally.md) to run a multi-project application. 
If you haven't installed tye, follow the [Getting Started Instructions](https://github.com/dotnet/tye/blob/main/docs/getting_started.md) to install tye.

### Tips
- How to use [`tye run`](https://github.com/dotnet/tye/blob/main/docs/reference/commandline/tye-run.md)?
- How to access tye [Tye Dashboard](http://127.0.0.1:8000/) after `try run`?

## Required proejcts
* [Azure EventGrid Simulator (Run on local)](https://github.com/hasulab/Azure.EventGrid.Simulator.Sample)
	```
	git clone https://github.com/hasulab/Azure.EventGrid.Simulator.Sample.git
	```
	
	You will need a self signed certificate to run Azure EventGrid Simulator. Please check appsettings. 
	
	#### Tips
	- How to Generate a [self-signed certificate using PowerShell script](https://gist.github.com/hasmukhlalpatel/ed46bc73c7da708daafe3e566ee8f8d2)
	- How to access [Azure EventGrid Simulator homepage](https://localhost:5002/) after `try run`?

* [Azure KeyVault Simulator (Run on local)](https://github.com/hasulab/Azure.KeyVault.Simulator.Sample)
	```
	git clone https://github.com/hasulab/Azure.KeyVault.Simulator.Sample.git
	```

	#### Tips
	- How to access [Azure KeyVault Simulator homepage](https://localhost:5006/) after `try run`?

* [Azure Azure Cosmos DB Emulator (Intall & Run on local)](https://learn.microsoft.com/en-us/azure/cosmos-db/local-emulator?tabs=ssl-netstd21)
	or [run on Docker](https://learn.microsoft.com/en-us/azure/cosmos-db/docker-emulator-windows?tabs=cli)
	```
	docker pull mcr.microsoft.com/cosmosdb/windows/azure-cosmos-emulator
	```

	#### Tips
	- How to access [Azure Cosmos DB Emulator homepage]( https://localhost:8081/_explorer/index.html)?

* [Data API builder for Azure Databases](https://github.com/Azure/data-api-builder/blob/main/docs/getting-started/getting-started.md) generates REST and GraphQL endpoints for database objects, you need to have a database ready for the tutorial. You can choose either a relational or non-relational database.
	To install on local 
	```
	dotnet tool install --global Microsoft.DataApiBuilder
	```

	#### Tips
	- How to setup [REST and GraphQL endpoints for Azure Cosmos DB Emulator](https://github.com/Azure/data-api-builder/blob/main/docs/getting-started/getting-started-azure-cosmos-db.md)?
	- Setup 
	```
	cd  graphql
	dab init --database-type "cosmosdb_nosql" --graphql-schema schema.gql --cosmosdb_nosql-database titanStoreDB --connection-string "AccountEndpoint=https://localhost:8081/;AccountKey=REPLACEME;" --host-mode "Development"
	
	dab add Item --source items --permissions "anonymous:*"
	dab add Supplier --source suppliers --permissions "anonymous:*"
	
	dab start
	```