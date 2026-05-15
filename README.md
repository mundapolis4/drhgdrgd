appsettings.json:

```
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=zoo;Trusted_Connection=True;"
  },
```

Scaffolding:

```
Scaffold-DbContext "Name=ConnectionStrings:DefaultConnection" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models -DataAnnotations -Context ApplicationDbContext -ContextDir Data
```

Program.cs:

```
var connectionString = builder.Configuration.GetConnectionString("DefaultConnection") ?? throw new InvalidOperationException("Connection string: default connection not found!");

builder.Services.AddDbContext<ApplicationDbContext>(options => options.UseSqlServer("ConnectionString"));

app.UseSwaggerUI(options =>
{
  options.SwaggerEndpoint("/openapi/v1.json", "API v1");
});
```

launchSettings.json:

```
"launchBrowser": true,
"launchUrl": "swagger",
```
