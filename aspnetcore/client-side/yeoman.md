---
title: Building projects with Yeoman in ASP.NET Core | Microsoft Docs
author: spboyer
description: This article walks through building an ASP.NET Core web application using the Yeoman generator on macOS.
keywords: ASP.NET Core, Yeoman, Cross Platform, yo aspnet
ms.author: spboyer
manager: wpickett
ms.date: 02/21/2017
ms.topic: article
ms.assetid: fda0c2a8-1743-4505-be1a-7f8ceeef8647
ms.technology: aspnet
ms.prod: asp.net-core
uid: client-side/yeoman
---
# Introduction to building projects with Yeoman in ASP.NET Core

[Yeoman](http://yeoman.io/) is a project scaffolding system for creating many kinds of applications. The Yeoman generator for ASP.NET Core contains a variety of project templates for starting a new web, MVC, or console application.

## Install Node.js, npm, and Yeoman

### Prerequisites

Node.js and npm are required for Yeoman. Download from [Node.js](https://nodejs.org/en/). The installer includes [Node.js](https://nodejs.org/en/) and [npm](https://www.npmjs.com/). Bower is also required for installing UI components like stylesheets.

To install Yeoman and Bower run the following command:

```console
npm install -g yo bower
```

>[!Note]
>If you get the error `npm ERR! Please try running this command again as root/Administrator.` on macOS, run the following command using [sudo](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man8/sudo.8.html): `sudo npm install -g yo bower`

From a command prompt, install the ASP.NET generator:

```console
npm install -g generator-aspnet@0.2.6
```

> [!NOTE]
> If you get a permission error, run the command under `sudo` as described above.

The `–g` flag installs the generator globally, so that it can be used from any path.

## Create an ASP.NET app

Run the ASP.NET generator for `yo`

```console
yo aspnet
```

The generator displays a menu. Arrow down to the **Web Application Basic [without Membership and Authorization]** project and tap **Enter**:

![Command window: What type of application do you want to create? Menu of application types](yeoman/_static/yeoman-yo-aspnet.png)

Select Bootstrap as the UI Framework and tap **Enter**.

Use "**MyWebApp**" for the app name and then tap **Enter**.

Yeoman will scaffold the project and its supporting files. Suggested next steps are also provided in the form of commands.

![Command window: What's the name of your ASP.NET application? Command prompt](yeoman/_static/yeoman-yo-aspnet-created.png)

The [ASP.NET generator](https://www.npmjs.com/package/generator-aspnet) creates ASP.NET Core projects that can be loaded into Visual Studio Code, Visual Studio, or run from the command line.

## Restore, build, and run

Follow the suggested commands by changing directories to the `MyWebApp` directory. Then run `dotnet restore`.

![Command window](yeoman/_static/dotnet-restore.png)

Build and run the app using `dotnet build` and `dotnet run`:

![Command window](yeoman/_static/dotnet-build-run.png)

At this point you can navigate to the URL shown to test the newly created ASP.NET Core app.

## Client-side packages

The front end resources are provided by the templates from the yeoman generator using the [Bower](bower.md) client-side package manager, adding *bower.json* and *.bowerrc* files to restore client-side packages using the [Bower](bower.md) client-side package manager.

The [BundlerMinifier](https://github.com/madskristensen/BundlerMinifier/wiki) component is also included by default for ease of concatenation (bundling) and minification of CSS, JavaScript and HTML.

## Building and running from Visual Studio

You can load your generated ASP.NET Core web project directly into Visual Studio, then build and run your project from there. Follow the instructions above to scaffold a new ASP.NET Core app using yeoman. This time, choose **Web Application** from the menu and name the app `MyWebApp`.

Open Visual Studio. From the File menu, select Open ‣ Project/Solution.

In the Open Project dialog, navigate to the *project.json* file, select it, and click the **Open** button. In the Solution Explorer, the project should look something like the screenshot below.

![Files and folders of a new project in Solution Explorer](yeoman/_static/yeoman-solution.png)

Yeoman scaffolds a MVC web application, complete with both server- and client-side build support. Server-side dependencies are listed under the **References** node, and client-side dependencies in the **Dependencies** node of Solution Explorer. Dependencies are restored automatically when the project is loaded.

![Under the Dependencies node in the Solution Explorer tree view, the Bower folder is open listing its dependencies.](yeoman/_static/yeoman-loading-dependencies.png)

When all the dependencies are restored, press **F5** to run the project. The default home page displays in the browser.

![Web application open in Microsoft Edge](yeoman/_static/yeoman-home-page.png)

## Restoring, building, and hosting from a command line

You can prepare and host your web application using the [.NET Core](https://microsoft.com/net/core) command-line interface.

At a command prompt, change the current directory to the folder containing the project (that is, the folder containing the *project.json* file):

```console
cd src\MyWebApp
```

Restore the project's NuGet package dependencies:

```console
dotnet restore
```

Run the application:

```console
dotnet run
```

The cross-platform [Kestrel](../fundamentals/servers/kestrel.md) web server will begin listening on port 5000.

Open a web browser, and navigate to `http://localhost:5000`.

![Web application open in Microsoft Edge](yeoman/_static/yeoman-home-page_5000.png)

## Adding to your project with sub generators

You can add new generated files using Yeoman even after the project is created. Use [sub generators](https://www.github.com/omnisharp/generator-aspnet#sub-generators) to add any of the file types that make up your project. For example, to add a new class to your project, enter the `yo aspnet:Class` command followed by the name of the class. Execute the following command from the directory in which the file should be created:

```console
yo aspnet:Class Person
```

The result is a file named Person.cs with a class named `Person`:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace MyWebApp
{
    public class Person
    {
        public Person()
        {
        }
    }
}
```

## Additional resources

* [Servers (Kestrel and WebListener)](../fundamentals/servers/index.md)

* [Your First ASP.NET Core Application on a Mac Using Visual Studio Code](../tutorials/your-first-mac-aspnet.md)

* [Fundamentals](../fundamentals/index.md)
