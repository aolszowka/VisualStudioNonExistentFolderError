# VisualStudioNonExistentFolderError

In Visual Studio 2019 Enterprise as of 16.2.2 it is possible to get a CSPROJ File in a state where you cannot add files into it via Visual Studio Like So:

![](Issue/NonExistentFolderCannotBeFound.gif)

Here is the text of the error:

```text
---------------------------
Microsoft Visual Studio
---------------------------
The system cannot find the path specified.
---------------------------
OK
---------------------------

```

The root cause of the problem is that the CSPROJ File has this directive:

```xml
  <ItemGroup>
    <Folder Include="NonExistentFolder\" />
  </ItemGroup>
```

However in the working copy this folder does not exist.

This causes Visual Studio to correctly throw an error indicating that the system cannot find the path specified but it does not indicate what path was not found.