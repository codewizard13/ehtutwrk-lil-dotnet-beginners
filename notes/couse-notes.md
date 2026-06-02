# COURSE NOTES: .NET Development for Beginners (2024)


## Video 02

- **#GOTCHA:** Solution Explorer doesn't show up as in 2:10

- **#SOLVED:** Her instructions only work if you don't already have a folder open. Start in a blank VSCODE window.
- Here's my code following her simple interactive example
  - #OBSERVATION: This is very similar in syntax to **PowerShell**

```cs
Console.WriteLine("What is your name?");
var name = Console.ReadLine();
var currentDate = DateTime.Now;
Console.WriteLine($"{Environment.NewLine}Hello, {name}, on {currentDate:d}");
Console.Write($"{Environment.NewLine}Press any key to exit...");
```

## Video 03

- NuGet.org

---

## #SUMMARY/TLDR:

> The course screenshot is just showing Visual Studio’s project tree, not actual folders, so `Dependencies` and `Frameworks` aren’t real directories on disk. In VS Code you just have Program.cs, the `.csproj`, and maybe an `.sln`; `slnx` is basically VS Code’s own metadata, while `sln` is the normal solution file you want for compatibility. In short: don’t sweat the missing folders, use the regular `.csproj`/`.sln` console app setup and treat the UI difference as just different editor plumbing.

![Screenshot of Solution Explorer looking different than the VSCODE 'Explorer' sidebar](/_pix/screens/screen_01_solution-explorer-vid3.png)

## #GOTCHA

- `Dependencies` and `Frameworks` are IDE view nodes, not real folders on disk.
- VS Code shows `Explorer`, while Visual Studio shows `Solution Explorer`; same project, different UI.
- `Solution Explorer` can display package/reference groups even when those are not separate filesystem directories.
- `*.slnx` is not the same as a standard solution file and is mainly VS Code metadata.
- Newer .NET templates may look different in 2026 than the course screenshot from 2024.

## #SOLUTIONS

- Treat `Dependencies` / `Frameworks` as a tree view representation, not actual project directories.
- Use Program.cs + `.csproj` + optional `*.sln` for a normal console app project.
- Prefer `*.sln` for portability and compatibility across tools.
- Open the `.sln` or `.csproj` in VS Code with the C# extension to get the richer project experience.
- If you want the same behavior as the instructor, use the standard `dotnet new console` / `dotnet new sln` workflow and ignore the VS Code-specific `*.slnx` unless asked.


---

### Steps to install and run the a NuGet package:

**Create Starter Console App**

1. `CTRL + SHIFT + P` > .NET: New Project > Console App > [MyPasswordGenerator (or whatever your app name is)]
2. Select whether to save in the current/default folder or a different folder
3. Select **sln**
4. Now your starter app is installed! :)

**Install the Password Generator Package from NuGet**

5. Navigate in a browser to: https://www.nuget.org/packages/PasswordGenerator#readme-body-tab
6. Copy the `.NET CLI` snippet into your terminal
7. CD into MyPasswordGenerator/ or whatever your project folder is
8. Paste and run the following `.NET CLI` snippet:

```cs
dotnet add package PasswordGenerator --version 3.0.0
```
9. Add the following in `Program.cs`, and then type `dotnet run` in the terminal and it might take a few seconds on the first run but it should generate and display a complex password. Each time you run it will generate a different password.

- #ERICS_CODE

```cs
using PasswordGenerator;

var pwd = new Password();
var password = pwd.Next();

Console.WriteLine(password.ToString());
```