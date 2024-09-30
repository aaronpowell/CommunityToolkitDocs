---
title: Azure Static Web Apps emulator
author: aaronpowell
description: A .NET Aspire hosting integration for the Azure Static Web Apps emulator.
ms.date: 10/01/2024
---

## Overview

This is a .NET Aspire Integration for using the [Azure Static Web App CLI](https://learn.microsoft.com/azure/static-web-apps/local-development) to run Azure Static Web Apps locally using the emulator.

It provides support for proxying both the static frontend and the API backend using resources defined in the AppHost project.

> [!NOTE]
> This does not support deployment to Azure Static Web Apps.

## Usage

> [!NOTE]
> This integration requires the Azure Static Web Apps CLI to be installed. You can install it using the following command:

    ```bash
    npm install -g @azure/static-web-apps-cli
    ```

```csharp
var builder = DistributedApplication.CreateBuilder(args);

// Define the API resource
var api = builder.AddProject<Projects.Aspire_CommunityToolkit_StaticWebApps_ApiApp>("api");

// Define the frontend resource
var web = builder
    .AddNpmApp("web", Path.Combine("..", "Aspire.CommunityToolkit.StaticWebApps.WebApp"), "dev")
    .WithHttpEndpoint(env: "PORT")
    .WithExternalHttpEndpoints();

// Create a SWA emulator with the frontend and API resources
_ = builder
    .AddSwaEmulator("swa")
    .WithAppResource(web)
    .WithApiResource(api);

builder.Build().Run();
```

### Configuration

- `Port` - The port to run the emulator on. Defaults to `4280`.
- `DevServerTimeout` - The timeout (in seconds) for the frontend dev server. Defaults to `60`.
