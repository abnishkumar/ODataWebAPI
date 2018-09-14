# ODataWebAPI

Step By Step Create OData Web API

1.Create Empty Web API Project.
2.Install-Package Microsoft.AspNet.Odata
3.Install-Package EntityFramework
4.Controller class inherit from ODataController
5. // Configure the OData Endpoint

            ODataModelBuilder builder = new ODataConventionModelBuilder();
            builder.EntitySet<Product>("Products"); // you can add EntitySet DbSet
            config.MapODataServiceRoute(
                routeName: "ODataRoute",
                routePrefix: null,
            model: builder.GetEdmModel());
            
NOTE:-OData configuration always below the routing Congiguration
// Web API configuration and services

            // Web API routes
            config.MapHttpAttributeRoutes();

            config.Routes.MapHttpRoute(
                name: "DefaultApi",
                routeTemplate: "api/{controller}/{id}",
                defaults: new { id = RouteParameter.Optional }
            );

            // Configure the OData Endpoint
            ODataModelBuilder builder = new ODataConventionModelBuilder();
            builder.EntitySet<Product>("Products");
            config.MapODataServiceRoute(
                routeName: "ODataRoute",
                routePrefix: null,
            model: builder.GetEdmModel());
            
            
