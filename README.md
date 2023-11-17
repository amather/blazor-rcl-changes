
# Steps to reproduce

## Create solution with Balzor & RCL projects

- `dotnet new sln -n blazor-changes-bug`
- `dotnet new blazor --interactivity Auto  --empty true --auth None --all-interactive true --no-https -n MyApp.Web`
- `dotnet sln blazor-changes-bug.sln add MyApp.Web/MyApp.Web/MyApp.Web.csproj`
- `dotnet sln blazor-changes-bug.sln add MyApp.Web/MyApp.Web.Client/MyApp.Web.Client.csproj`

- `dotnet new razorclasslib -n MyApp.Web.Shared`
- `dotnet sln blazor-changes-bug.sln add MyApp.Web.Shared/MyApp.Web.Shared.csproj`

- configure `MyApp.Web` and `MyApp.Web.Client` to reference `MyApp.Web.Shared`

## Configure Shared project

- move `Home.razor` to MyApp.Web.Shared
- configure `MyApp.Web.Client\Routes.razor` with `AdditionalAssemblies`
- configure `MyApp.Web\Program.cs` with `AddAdditionalAssemblies()`

- Run (Ctrl-F5)
- Change `<h1>` to `<h1>Hello, world! 2</h1>` in `Home.razor`
- Run (Ctrl-F5)
- page will read `Hello, world! 2`, a second later will flip to `Hello, world!` 