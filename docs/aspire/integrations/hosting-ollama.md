---
title: Ollama hosting
author: aaronpowell
description: A .NET Aspire hosting integration for hosting Ollama models using the Ollama container.
ms.date: 10/01/2024
---

## Overview

An Aspire component leveraging the [Ollama](https://ollama.com) container with support for downloading a model on startup.

## Usage

Use the static `AddOllama` method to add this container component to the application builder.

```csharp
// The distributed application builder is created here

var ollama = builder.AddOllama("ollama").AddModel("llama3");

// The builder is used to build and run the app somewhere down here
```

### Configuration

- The `name` is what gets displayed in the Aspire orchestration app against this component.
- The `port` is provided randomly by Aspire. If for whatever reason you need a fixed port, you can set that here.

## Downloading the LLM

When the Ollama container for this component first spins up, this component will download the LLM(s). The progress of this download will be displayed in the State column for this component on the Aspire orchestration app.

> [!IMPORTANT]
> Keep the .NET Aspire orchestration app open until the download is complete, otherwise the download will be cancelled.

## Caching the LLM

The LLM(s) will be downloaded into the container which Ollama is running from, and by default this container is ephemeral. If you need to persist the LLM(s) across container restarts, you will need to mount a volume into the container using the `AddDataVolume` method.

```csharp
var ollama = builder.AddOllama("ollama").AddModel("llama3").AddDataVolume();
```

## Accessing the Ollama server in other services

The Ollama hosting integration exposes the endpoint of the Ollama server as a connection string that can be accessed from other services in the application.

```csharp
var connectionString = builder.Configuration.GetConnectionString("ollama");
```

## Open WebUI support

The Ollama integration also provided support for running [Open WebUI](https://openwebui.com/) and having it communicate with the Ollama container.

```csharp
var ollama = builder.AddOllama("ollama").AddModel("llama3").WithOpenWebUI();
```
