### eShop On Web Notes

needed .NET Core 2.2 [download](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-2.2.104-windows-x64-installerd)

get current version: `git pull upstream master`

Build OK, but resharper has errors, eg: AccountContoller.SignIn() has no View (it doesn't. hmn... come back to this.)

Set up for use with SQL Server (rather then inMemory DB) by updating appsettings.json `Data Source=.\\SQLDEV17`