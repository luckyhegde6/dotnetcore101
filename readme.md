# .NET commands
- If you want a detailed list of all commands, enter ```dotnet --help ``` in the terminal.

## How to install a package
- You use the ```dotnet add package <dependency name> ```command to install a normal dependency that's meant to be used as part of your application.

## After installation
The installed packages are listed in the dependencies section of your .csproj file. If you want to see what packages are in the folder, you can enter ```dotnet list package```.

- Including transitives will allow you to see dependencies along with all the packages you've installed. If you run ``` dotnet list package --include-transitive ```, 

## Restore dependencies
When you create or clone a project, the included dependencies are not downloaded or installed until you build your project. You can manually restore dependencies as well as project-specific tools that are specified in the project file by running the ``` dotnet restore ``` command. In most cases, you don't need to explicitly use the command. NuGet restore is run implicitly, if necessary, when you run commands like ``` new, build, and run ```.

## Clean up dependencies

- To remove a package from your project, you use the remove command like so: ```dotnet remove package <name of dependency> ```. This command will remove the package from the .csproj file for your project.

## Create a sample .NET project
To set up a .NET project to work with dependencies, we'll use Visual Studio Code. Visual Studio Code includes an integrated terminal, which makes creating a new project easy. If you don't want to use another code editor, you can run the commands in this module in a terminal.

    In Visual Studio Code, select File > Open Folder.

    Create a new folder named DotNetDependencies in the location of your choice, and then select Select Folder.

    Open the integrated terminal from Visual Studio Code by selecting View > Terminal from the main menu.

    In the terminal window, copy and paste the following command.

``` dotnet new console -f net6.0 ```
This command creates a Program.cs file in your folder with a basic "Hello World" program already written, along with a C# project file named **DotNetDependencies.csproj**.

In the terminal window, copy and paste the following command to run the "Hello World" program.
``` dotnet build && dotnet run ```


## Set up Visual Studio Code for .NET debugging

Open Program.cs. The first time you open a C# file in Visual Studio Code, you get a prompt to install recommended extensions for C#. Select the Install button in the prompt.

## Manage dependency updates in your .NET project
 ### Find and update outdated packages

The ``` dotnet list package --outdated ``` command lists outdated packages. This command can help you learn when newer versions of packages are available. 

Here are the meanings of the names of the columns in the output:

   - Requested. The version or version range that you've specified.
   - Resolved. The actual version that has been downloaded for the project that matches the specified version.
   - Latest. The latest version available for update from NuGet.

The recommended workflow is to run these commands, in this order:

   - Run ``` dotnet list package --outdated ```. This command lists all the outdated packages. It provides information in the Requested, Resolved, and Latest columns.
   - Run ``` dotnet add package <package name> ```. If you run this command, it will try to update to the latest version. Optionally, you can pass in --version=<version number/range>.

### Update approach

As a .NET developer, you can communicate to .NET the update behavior that you want. Think about updating in terms of risk. Here are some approaches:
- Major version. I'm OK with updating to the latest major version as soon as it's out. I accept the fact that I might need to change code on my end.
- Minor version. I'm OK with a new feature being added. I'm not OK with code that breaks.
- Patch version. The only updates I'm OK with are bug fixes.

If you're managing a new or smaller .NET project, you can afford to be loose with how you define the update strategy. For example, you can always update to the latest version. For more complex projects, there's more nuance, but we'll save that for a future module.

In general, the smaller the dependency you're updating, the fewer dependencies it has and the more likely that the update process will be easy.

## Upgrade app dependencies

In the ProjectName.csproj file, look at the dependencies. It should look like this code.
    ``` <ItemGroup>
    <PackageReference Include="PackageName" Version="2.x.x" />
    </ItemGroup> ```
