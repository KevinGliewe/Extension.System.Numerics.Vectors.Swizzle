# Extension.System.Numerics.Vectors.Swizzle

[![NuGet Package](https://img.shields.io/nuget/v/Extension.System.Numerics.Vectors.Swizzle.svg)](https://www.nuget.org/packages/Extension.System.Numerics.Vectors.Swizzle)


Add Swizzling to float, Vector2, Vector3 and Vector4 as extension.
https://en.wikipedia.org/wiki/Swizzling_(computer_graphics)

## Installation

### Package Manager

```bash
Install-Package Extension.System.Numerics.Vectors.Swizzle
```

### .NET CLI

```bash
dotnet add package Extension.System.Numerics.Vectors.Swizzle
```

### PackageReference

```xml
<PackageReference Include="Extension.System.Numerics.Vectors.Swizzle" />
```

### Packet CLI

```bash
paket add Extension.System.Numerics.Vectors.Swizzle
```

## Example

```csharp
using System;
using System.Numerics;
using System.Diagnostics;

class Program
{
    static void Main(string[] args)
    {
        float pi = 3.14f;

        // Get Vector2 from float by requesting the first component twice
        Vector2 v2 = pi.XX();
        Debug.Assert(v2.X == pi);
        Debug.Assert(v2.Y == pi);

        v2.X = 1.0f;
        v2.Y = 3.0f;

        // Get Vector4 from Vector2 by requesting components and injecting new ones
        Vector4 v4 = v2.X_Y_(2.0f, 4.0f);
        Debug.Assert(v4.X == 1.0f);
        Debug.Assert(v4.Y == 2.0f);
        Debug.Assert(v4.Z == 3.0f);
        Debug.Assert(v4.W == 4.0f);

        // Copy the W and X component over to a Vector2
        v4.WX(ref v2);
        Debug.Assert(v2.X == 4.0f);
        Debug.Assert(v2.Y == 1.0f);
    }
}
```