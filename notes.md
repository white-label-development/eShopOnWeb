### eShop On Web Notes

needed .NET Core 2.2 [download](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-2.2.104-windows-x64-installerd)

get current version: `git pull upstream master`

Build OK, but resharper has errors, eg: AccountContoller.SignIn() has no View (it doesn't. hmn... come back to this.)



#### Startup.cs

Set up for use with SQL Server (rather then inMemory DB) by updating appsettings.json `Data Source=.\\SQLDEV17`
and ConfigureDevelopmentServices().

##### Slugify

[Slugify](https://github.com/ctolkien/Slugify) is used for creating safe routes and configured via
```
services.AddRouting(options =>
            {
                // Replace the type and the name used to refer to it with your own IOutboundParameterTransformer implementation
                options.ConstraintMap["slugify"] = typeof(SlugifyParameterTransformer);
            });
```

and

```
services.AddMvc(options =>
            {
                options.Conventions.Add(new RouteTokenTransformerConvention(new SlugifyParameterTransformer()));                
            }
```

TODO: grok this.


##### services.AddScoped

The usual services are registered via `services.AddScoped(x)`

ASIDE: https://andrewlock.net/using-scrutor-to-automatically-register-your-services-with-the-asp-net-core-di-container/ 


##### Razor pages WTF

Decides bring in Razor pages for Identity stuff
```
 .AddRazorPagesOptions(options =>
                {
                    options.Conventions.AuthorizePage("/Basket/Checkout");
                    options.AllowAreas = true;
                })
```

After an intial WTF I think I like Razor Pages as they are simpler than MVC.


ref: https://www.thereformedprogrammer.net/six-things-i-learnt-about-using-asp-net-cores-razor-pages/
ref: https://www.thereformedprogrammer.net/asp-net-core-razor-pages-how-to-implement-ajax-requests/#filter-cshtml-cs
ref: https://www.learnrazorpages.com/razor-pages/model-binding


##### AddHealthChecks

` services.AddHealthChecks()...`
TODO: grok this.


##### CreateIdentityIfNotCreated()

includes this `.AddDefaultUI(UIFramework.Bootstrap4)` which I think creates the Identity razor page scaffolding.







