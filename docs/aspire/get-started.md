---
title: Getting Started with the .NET Aspire Community Toolkit
author: aaronpowell
description: The toolkit is available as a set of NuGet packages that can be added to any existing or new .NET Aspire project.
ms.date: 10/01/2024
---

# Getting Started with the .NET Aspire Community Toolkit

This article covers how to get started using the packages provided as part of the .NET Aspire Community Toolkit project.

## Adding the Hosting package(s)

The toolkit is available as a set of NuGet packages that can be added to any existing or new project using Visual Studio.

1. Open an existing project, or create a new project as per the [.NET Aspire setup documentation](/dotnet/aspire/get-started/build-your-first-aspire-app)

2. In the Solution Explorer panel, right click on your **AppHost** project name, navigate to **Add** and select **.NET Aspire Packages**. Search for **Aspire.CommunityToolkit**, and choose the desired NuGet Package from the list.

   ![Add .NET Aspire Packages...](images/get-started/manage-nuget.png "Right click on the solution and select 'Add .NET Aspire Packages...'")

3. Choose the integrations that are most appropriate for your needs from the available packages.

4. Once the packages have been added, you can add them to the `DistribedApplicationBuilder` and provide them as resources to your application.

## Other resources

The [.NET Aspire Community Toolkit GitHub Repository](https://github.com/CommunityToolkit/Aspire/tree/main/samples) contains the source code for a sample application that is designed to show how you can use the toolkit to build a .NET Aspire application. **Please note that you will be required to clone or download the repository and compile the source code in order to run the sample application.**

We recommend developers who are new to .NET Aspire to visit the [.NET Aspire](/dotnet/aspire/) documentation.

Visit the [.NET Aspire Community Toolkit GitHub Repository](https://github.com/CommunityToolkit/Aspire) to see the current source code, what is coming next, and clone the repository. Community contributions are welcome!
