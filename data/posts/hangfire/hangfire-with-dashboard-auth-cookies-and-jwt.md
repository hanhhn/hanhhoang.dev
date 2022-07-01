---
title: 'Hangfire with authorization Jwt and Cookeis'
date: '2022-06-17'
tags: ['hangfire']
draft: false
summary: 'Easy way to touch hangfire!!!! About hangfire, install, intgate dashboard + authen'
---

## Introduce

> An easy way to perform background processing in .NET and .NET Core applications. No Windows Service or separate process required. Backed by persistent storage. Open and free for commercial use.

Hangfire là 1 open source framework trên dotNET cho phép bạn:

1. Recurring Tasks

Recurring job processing has never been easier
Register when start website

2. Queue-based Processing

Create a job and execute immediately

3. Schedule

Job will execute for a specified time

## Licenses

> Hangfire software is an open-source software that is multi-licensed under the terms of the licenses listed.

1. LGPL v3 License
2. Commercial Licenses
3. Third-party Notices

## Nuget

1. Hangfire
2. Hangfire.Core
3. Hangfire.AspNet
4. Hangfire.AspNetCore
5. Hangfire.InMemory
6. Hangfire.NetCore
7. Hangfire.SqlServer
8. Hangfire.SqlServer.Msmq

## Backed by Persistent Storage

1. SQL Server
2. Redis
3. In-Memory (preview) - NOT RECOMMEND

## Support

1. .NET Framework 4.5 or later
2. .NET Core 1.0 or later

## Install

```
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
  <PackageReference Include="Hangfire.Core" Version="__*" />
  <PackageReference Include="Hangfire.SqlServer" Version="__.*" />
  <PackageReference Include="Hangfire.AspNetCore" Version="__.*" />
</ItemGroup>
```

## Dependency Injection
```
// Add Hangfire services. UseHangfireInMemory is config in appsetting.json
if (UseHangfireInMemory)
{
  services.AddHangfire(configuration =>
  {
      configuration.UseMemoryStorage();
  });
}
else
{
  services.AddHangfire(configuration => configuration
    .SetDataCompatibilityLevel(CompatibilityLevel.Version_170)
    .UseSimpleAssemblyNameTypeSerializer()
    .UseRecommendedSerializerSettings()
    .UseSqlServerStorage(AppSettings.Instance.HangfireConnectionString, new SqlServerStorageOptions
    {
      CommandBatchMaxTimeout = TimeSpan.FromMinutes(5),
      SlidingInvisibilityTimeout = TimeSpan.FromMinutes(5),
      QueuePollInterval = TimeSpan.Zero,
      UseRecommendedIsolationLevel = true,
      DisableGlobalLocks = true
    }));
}
```

```
app.UseEndpoints(endpoints =>
{
    app.UseHangfireDashboard("/hangfire", new DashboardOptions
    {
        Authorization = new[] { new HangfireDashboardAuthorizationFilter() }
    });
});
```

## Hangfire Dashboard and Authen
```
public static IServiceCollection AddJwtAuthentication(this IServiceCollection services, IConfiguration config)
{
  services
  .AddAuthentication(options =>
  {
    options.DefaultScheme = "Bearer,Cookies";
    options.DefaultChallengeScheme = "Bearer,Cookies";
  })
  .AddJwtBearer("Bearer", o =>
  {
    //o.SaveToken = true;
    o.TokenValidationParameters = new TokenValidationParameters
    {
      IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(AppSettings.Configs["JwtSettings:Key"])),
      ValidateIssuerSigningKey = true,
      ValidateIssuer = false,
      ValidateLifetime = true,
      ValidateAudience = false,
      ClockSkew = TimeSpan.FromMinutes(15)
    };

    o.Events = new JwtBearerEvents
    {
      OnTokenValidated = async ctx =>
      {
        /* validate token here*/
      },
      OnAuthenticationFailed = async ctx =>
      {
          logger.LogError($"Authen failed: {ctx.Exception}");
      }
    };
  })
  .AddCookie("Cookies", options =>
  {
    options.ExpireTimeSpan = TimeSpan.FromMinutes(int.Parse(AppSettings.Configs["JwtSettings:AccessExpireMinutes"]));
    options.SlidingExpiration = true;
  })
  .AddPolicyScheme("Bearer,Cookies", "Bearer,Cookies", options =>
  {
    // runs on each request
    options.ForwardDefaultSelector = context =>
    {
      // filter by auth type
      string authorization = context.Request.Headers[HeaderNames.Authorization];
      if (!string.IsNullOrEmpty(authorization) && authorization.StartsWith("Bearer "))
          return "Bearer";

      // otherwise always check for cookie auth
      return "Cookies";
    };
  });

  return services;
}

```

```
public class HangfireDashboardAuthorizationFilter : IDashboardAuthorizationFilter
{
  private const string HangfirePermissionRole = "Hangfire";

  public bool Authorize(DashboardContext context)
  {
    var httpContext = context.GetHttpContext();
    var isAuthenticated = httpContext.User.Identity.IsAuthenticated;

    if (isAuthenticated)
    {
        var identity = (ClaimsIdentity)httpContext.User.Identity;
        var claim = identity.Claims.FirstOrDefault(x => x.Type == ClaimTypes.Permission);

        if (claim != null && claim.Value.Split(",").Contains(HangfirePermissionRole))
        {
            return isAuthenticated;
        }
        else
        {
            httpContext.Response.StatusCode = (int)HttpStatusCode.Unauthorized;
            httpContext.Response.ContentType = "Oops! Unauthorized!";
            return false;
        }
    }

    return isAuthenticated;
  }
}
```

## Background Methods

1. BackgroundJob.Enqueue
2. BackgroundJob.Schedule
3. RecurringJob.AddOrUpdate
