<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg" width="88" alt="Logo de Java">

  # DPA · Control de Personal Retirado

  **Aplicación de escritorio para registrar y dar seguimiento a trámites de beneficios sociales.**

  ![Java](https://img.shields.io/badge/Java-Swing-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
  ![MySQL](https://img.shields.io/badge/MySQL-5.1%20Connector-4479A1?style=flat-square&logo=mysql&logoColor=white)
  ![JasperReports](https://img.shields.io/badge/JasperReports-6.0.0-2F6DB5?style=flat-square)
  ![NetBeans](https://img.shields.io/badge/NetBeans-Ant-1B6AC6?style=flat-square&logo=apachenetbeanside&logoColor=white)
</div>

---

## Sobre el proyecto

`DPA_Control_Personal_Retirado` centraliza el seguimiento de beneficios sociales asociados a jubilación, fallecimiento o retiro. La aplicación permite mantener un registro anual de cada trámite, consultar su información y controlar fechas, documentación pendiente y valores requeridos desde una interfaz gráfica de escritorio.

El reporte incluido identifica como contexto de uso al **Departamento de Personal Académico de la Universidad Mayor de San Simón**. La información se almacena en MySQL y puede consultarse por gestión o por nombre.

## Funcionalidades principales

- Registro de trámites con número correlativo por gestión, nombre y motivo.
- Clasificación por **jubilación**, **fallecimiento** o **retiro**.
- Seguimiento de la fecha del motivo, recepción de documentos y envío a Asesoría Legal.
- Control de documentación pendiente y valores requeridos.
- Consulta de registros por año, ordenados por número.
- Búsqueda parcial por nombre dentro de la gestión seleccionada.
- Modificación y eliminación de registros desde la tabla principal.
- Generación y visualización de reportes anuales mediante JasperReports.
- Identificación visual de los motivos en la tabla mediante colores.

## Flujo de trabajo

1. Se selecciona una gestión entre el año actual y los nueve años anteriores.
2. La aplicación carga los registros de esa gestión desde MySQL y calcula el siguiente número correlativo.
3. El usuario registra un trámite o selecciona uno existente para actualizarlo o eliminarlo.
4. La información puede filtrarse por nombre sin salir de la gestión activa.
5. El reporte anual reúne los registros de la gestión seleccionada y se abre en el visor de JasperReports.

## Información gestionada

| Campo | Uso |
| --- | --- |
| Gestión y número | Organización correlativa de los registros por año |
| Nombre | Identificación de la persona vinculada al trámite |
| Motivo | Jubilación, fallecimiento o retiro |
| Fechas de seguimiento | Motivo, recepción documental y envío a Asesoría Legal |
| Documento pendiente | Detalle de documentación aún no remitida |
| Valores requeridos | Estado o requisito asociado al trámite |

## Tecnologías

| Tecnología | Función en el proyecto |
| --- | --- |
| Java SE | Lenguaje principal de la aplicación |
| Swing | Interfaz gráfica de escritorio |
| JDBC + MySQL Connector/J 5.1.47 | Acceso y persistencia de datos en MySQL |
| JasperReports 6.0.0 | Construcción y visualización del reporte anual |
| iText 5.5.4 | Dependencia de soporte para la generación de documentos |
| Apache Ant / NetBeans | Configuración de compilación y empaquetado |

## Estructura principal

```text
├── src/
│   ├── registro/
│   │   ├── Formulario.java       # Interfaz y operaciones de seguimiento
│   │   ├── Conexion.java         # Conexión JDBC con MySQL
│   │   └── colorearCelda.java    # Presentación visual de la tabla
│   └── reportes/
│       ├── Beneficio.jrxml        # Diseño editable del reporte
│       └── Beneficio.jasper       # Reporte compilado
├── dist/
│   ├── segundoDPAUV_1.jar         # Aplicación empaquetada
│   └── lib/                       # Dependencias de ejecución
├── nbproject/                     # Configuración del proyecto NetBeans
└── build.xml                      # Script de compilación Ant
```

## Persistencia de datos

La aplicación se conecta por JDBC a una instancia local de MySQL. El código espera una base de datos llamada `registros_beneficios` y trabaja con la tabla `beneficios`, cuyos campos corresponden a la información descrita anteriormente.

> [!IMPORTANT]
> El repositorio no incluye un volcado SQL ni un proceso de creación de la base de datos. Para utilizar la aplicación, la base y la tabla deben estar creadas previamente y la configuración de conexión de `Conexion.java` debe coincidir con el entorno local.

## Ejecución

El repositorio incluye una distribución compilada con sus bibliotecas. Con MySQL en funcionamiento y la base de datos requerida disponible:

```bash
cd dist
java -jar segundoDPAUV_1.jar
```

También puede abrirse como proyecto Java SE en NetBeans. La clase de inicio configurada es `registro.Formulario`; las referencias locales a las bibliotecas deben resolverse según el entorno antes de compilar nuevamente.

## Contexto

El sistema está orientado al control operativo de beneficios sociales del personal retirado. El formato de reporte incorporado corresponde al Departamento de Personal Académico de la Universidad Mayor de San Simón y consolida, por gestión, el avance documental de los trámites registrados.
