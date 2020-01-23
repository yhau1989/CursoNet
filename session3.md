
# Sesión 3

[início](/README.md)

### Crear Windows Services con Visual Studio 2013 o posteriores

## Arquitectura de la solución en Visual Studio

* Crear solución en blanco
![](/images/2020-01-23-14-12-46.png)

* Añadir un nuevo proyecto (Class Librery) a la solución **capa logica**
![](/images/2020-01-23-14-13-25.png)

![](/images/2020-01-23-14-14-10.png)

* Añadir un nuevo proyecto (Console) a la solución **Testing**
![](/images/2020-01-23-14-14-42.png)


* Añadir un nuevo proyecto (Windows Services) a la solución **Servicion de Windows**
![](/images/2020-01-23-14-16-17.png)

Así se dbe ver el proyecto
![](/images/2020-01-23-14-21-09.png)


## Clases a Usar

* Libreria

```csharp
namespace Logical
{
    public class Logueo
    {
        public string sourceFile { get; set; } = null;
        public string nameFile { get; set; } = null;

        public string WriteArchivo(string mensaje)
        {
            string file = null;
            try
            {
                System.IO.File.WriteAllText($"{this.sourceFile}{this.nameFile}.txt", mensaje);
                file = $"Se grabo el archivo {this.nameFile}.txt con exito";
            }
            catch (Exception ex)
            {
                file = $@"Error al generar el archivo: {System.Environment.NewLine} 
                          Detalle de error: {ex.Message} {System.Environment.NewLine}
                          Error en {ex.Source}";
            }

            return file;
        }

        

    }
}

```
```csharp
namespace Logical
{
    public class ClaseTest
    {
        public string nombres { get; set; }
        public string apellidos { get; set; }
        public int edad { get; set; }
        public string mensaje { get; set; }

        public ClaseTest(string _nombre, string _apellidos, int _edad, string _mensaje)
        {
            nombres = _nombre;
            apellidos = _apellidos;
            edad = _edad;
            mensaje = _mensaje;
            escribirArchivo();
        }

        public string escribirArchivo()
        {
            Logueo log = new Logueo() {
                nameFile = System.Configuration.ConfigurationManager.AppSettings[""].ToString(),
                sourceFile = getNameDocumentNow()
            };

            return log.WriteArchivo($@"
                Nombre: {nombres} {System.Environment.NewLine} 
                Apellidos: {apellidos} {System.Environment.NewLine} 
                Edad: {edad} {System.Environment.NewLine} 
                Mensaje: {mensaje} {System.Environment.NewLine} 
                Fecha: {DateTime.Now.ToString("ddMMyyyymmss")}
            ");
        }


        /// <summary>
        /// 
        /// </summary>
        /// <returns></returns>
        /// <![CDATA[ 
        /// Autor: Samuel Pilay Muñoz
        /// fecha creación: 2020-01-23 14:41:37
        /// ]]>	
        public string getNameDocumentNow() { return $"File_{DateTime.Now.ToString("ddMMyyyymmss")}"; }
    }
}
```


### Crear Web Apis (RestFull Services) con Visual Studio 2013 o posteriores


