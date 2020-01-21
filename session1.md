
# Sesión 1

[início](/README.md)

### Actualización Net Framework 4.6 y posteriores
 
 * La importancia de estar actualizado [versiones NET Framwork](https://dotnet.microsoft.com/download/dotnet-framework)
 * [Ditribuciones del framework](https://dotnet.microsoft.com/download) 
 * Leer el [Blog de .NET](https://devblogs.microsoft.com/dotnet/)


### Lenguaje C# versión 8, exploración, mejoras y nuevas funcionalidades, ejercicios

* Historia de las [versiones de c#](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-version-history)  
* [Version 8](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-8)

#### Null-coalescing assignment

```csharp
    List<int> numbers = null;
    int? i = null;

    numbers ??= new List<int>();
    numbers.Add(i ??= 17);
    numbers.Add(i ??= 20);

    Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
    Console.WriteLine(i);  // output: 17
```

#### $ - string interpolation
[version online](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated#code-try-0)
```csharp
    string name = "Mark";
    var date = DateTime.Now;

    // Composite formatting:
    Console.WriteLine("Hello, {0}! Today is {1}, it's {2:HH:mm} now.", name, date.DayOfWeek, date);
    // String interpolation:
    Console.WriteLine($"Hello, {name}! Today is {date.DayOfWeek}, it's {date:HH:mm} now.");
    // Both calls produce the same output that is similar to:
    // Hello, Mark! Today is Wednesday, it's 19:40 now.
```

    Comenzando con C # 8.0, puede usar los tokens $ y @ en cualquier orden: tanto $ @ "..." como @ $ "..." son cadenas textuales interpoladas válidas. En versiones anteriores de C #, el token $ debe aparecer antes que el token @.


**Practica**

[xml](https://www.w3schools.com/xml/note.xml)

[json](https://jsonapi.org/examples/)

### Habilitar y configurar IIS

* En [Windows Server](https://thesolving.com/es/sala-de-servidores/como-instalar-y-configurar-iis-en-windows-server-2012-r2/)
* En [Windows 7](https://norfipc.com/internet/instalar-usar-servidor-web-iis-windows.html)
* en [Winsdows 10](https://luisperis.com/instalar-iis-windows-10-5-minutos/)


### Uso de GitHub como almacén de código fuente para acelerar futuros desarrollos

[Guía](https://medium.com/@sthefany/primeros-pasos-con-github-7d5e0769158c) básica de [Git](https://git-scm.com/doc) y [Github](https://github.com/) para principiantes.