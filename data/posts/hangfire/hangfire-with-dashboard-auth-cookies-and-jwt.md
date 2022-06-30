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

## Hangfire Dashboard and Authen

## Background Methods

1. BackgroundJob.Enqueue
2. BackgroundJob.Schedule
3. RecurringJob.AddOrUpdate
