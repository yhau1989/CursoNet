
# Sesión 3

[início](/README.md)

### Crear Windows Services con Visual Studio 2013 o posteriores

## Arquitectura de la solución en Visual Studio

* Crear solución en blanco
![](/images/2020-01-23-14-12-46.png)

* Añadir un nuevo proyecto (Class Librery) a la solución **capa lógica**
![](/images/2020-01-23-14-13-25.png)

![](/images/2020-01-23-14-14-10.png)

* Añadir un nuevo proyecto (Console) a la solución **Testing**
![](/images/2020-01-23-14-14-42.png)


* Añadir un nuevo proyecto (Windows Services) a la solución **Servicio de Windows**
![](/images/2020-01-23-14-16-17.png)

Así se debe ver el proyecto
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



public partial class Service1 : ServiceBase
    {
        Timer tmrMailer;
        bool _ProcesandoMailer;

        public Service1()
        {
            InitializeComponent();
            Double interval = Double.Parse(ConfigurationSettings.AppSettings["intervalo_de_ejecucion"].ToString());
            tmrMailer = new Timer(interval);
            tmrMailer.Elapsed += new System.Timers.ElapsedEventHandler(tmrMailer_Elapsed);
        }

        protected override void OnStart(string[] args)
        {
            // TODO: Add code here to start your service.
            tmrMailer.Enabled = true;
            _ProcesandoMailer = false;
        }

        protected override void OnStop()
        {
            // TODO: Add code here to perform any tear-down necessary to stop your service.
            tmrMailer.Enabled = false;
            _ProcesandoMailer = true;
        }


        void tmrMailer_Elapsed(object sender, System.Timers.ElapsedEventArgs e)
        {
            this.process();

        }

        private void process()
        {
            if (!_ProcesandoMailer)
            {
                _ProcesandoMailer = true;

                try
                {
                    ClaseTest hcont = new ClaseTest("Samuel", "Pilay Muñoz", 30, "Esto es una clase");
                    hcont.escribirArchivo();
                }
                catch (Exception ex)
                {
                    throw ex;
                }
                finally
                {
                    _ProcesandoMailer = false;
                }

            }
        }
    }


```

#### Crear Windows Services Project Installer con Visual Studio 2013 o posteriores

[Manual](
https://www.c-sharpcorner.com/UploadFile/b7531b/create-simple-window-service-and-setup-project-with-installa/
)


[En caso de crear un instalador con problemas](windowService_bug_installer/) 


### Crear Web Apis (RestFull Services) con Visual Studio 2013 o posteriores


