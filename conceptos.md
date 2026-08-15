# Desarrollo e Implementación de Sistemas en la Nube — Biblioteca de Conceptos

Apuntes de referencia de la materia **Desarrollo e Implementación de Sistemas en la Nube**, IFTS N°11. Profesor: Emilio Dorion.

> Este archivo se organiza por concepto, no por orden cronológico de clases. El orden real en que se dio cada tema queda registrado en `bitacora.md` y en el historial de commits. La división real de la cátedra es por **Unidad**.

## Índice

- [Unidad 1 — Introducción a la computación en la nube](#unidad-1--introducción-a-la-computación-en-la-nube)
  - [1. ¿Qué es la nube?](#1-qué-es-la-nube)
  - [2. Origen y evolución histórica de la nube](#2-origen-y-evolución-histórica-de-la-nube)
    - [2.1 La idea original (décadas de 1960-1970)](#21-la-idea-original-décadas-de-1960-1970)
    - [2.2 Mainframes y nubes privadas](#22-mainframes-y-nubes-privadas)
    - [2.3 El nacimiento de la nube pública: AWS (2006)](#23-el-nacimiento-de-la-nube-pública-aws-2006)
    - [2.4 Panorama actual de proveedores](#24-panorama-actual-de-proveedores)
  - [3. Modelos de servicio en la nube: IaaS, PaaS y SaaS](#3-modelos-de-servicio-en-la-nube-iaas-paas-y-saas)
    - [3.1 IaaS — Infrastructure as a Service](#31-iaas--infrastructure-as-a-service)
    - [3.2 PaaS — Platform as a Service](#32-paas--platform-as-a-service)
    - [3.3 SaaS — Software as a Service](#33-saas--software-as-a-service)
    - [3.4 Comparación de responsabilidades entre modelos](#34-comparación-de-responsabilidades-entre-modelos)
  - [4. Tipos de nube: privada, pública e híbrida](#4-tipos-de-nube-privada-pública-e-híbrida)
  - [5. Comparación entre AWS y la infraestructura tradicional](#5-comparación-entre-aws-y-la-infraestructura-tradicional)
  - [6. Beneficios de la computación en la nube](#6-beneficios-de-la-computación-en-la-nube)
    - [6.1 Pago por uso (Pay-as-you-go)](#61-pago-por-uso-pay-as-you-go)
    - [6.2 Elasticidad y escalabilidad](#62-elasticidad-y-escalabilidad)
    - [6.3 Alta disponibilidad y distribución en regiones](#63-alta-disponibilidad-y-distribución-en-regiones)
    - [6.4 Eficiencia y time to market](#64-eficiencia-y-time-to-market)
    - [6.5 Acceso a tecnología reciente](#65-acceso-a-tecnología-reciente)
  - [7. DevOps (mención introductoria)](#7-devops-mención-introductoria)

---

## Unidad 1 — Introducción a la computación en la nube

### 1. ¿Qué es la nube?

La **nube** (*cloud computing*) es un modelo tecnológico que permite el acceso a recursos de cómputo (procesamiento, almacenamiento, redes, bases de datos, servicios de IA, etc.) a través de internet, sin que el usuario tenga que poseer ni administrar físicamente la infraestructura que los provee.

La idea central es que la infraestructura (hardware, software y red) está **virtualmente integrada**: para quien la usa es algo abstracto, no la toca ni la ve físicamente. Esto es distinto de tener una computadora o un servidor propio en casa o en la empresa, donde uno mismo compra, instala y mantiene el hardware.

Un segundo rasgo definitorio, más comercial que técnico, es la **entrega bajo demanda de potencia de cómputo**: en lugar de comprar hardware por adelantado y pagarlo esté o no en uso, se contrata la capacidad que se necesita en el momento en que se necesita, y se paga en función de eso (ver [Pago por uso](#61-pago-por-uso-pay-as-you-go)).

Esto tiene una consecuencia importante a nivel de negocio: la computación pasa de ser un **activo** que las empresas deben comprar y amortizar (servidores, licencias, hardware) a ser un **servicio** que se contrata y se paga según el consumo real.

### 2. Origen y evolución histórica de la nube

#### 2.1 La idea original (décadas de 1960-1970)

La idea de la computación como un servicio compartido no es nueva. Ya en la década de 1960, cuando internet ni siquiera existía en su forma moderna (recién estaba surgiendo un concepto embrionario de red, de uso exclusivamente militar), el científico **John McCarthy** planteó que en algún momento la informática podría ofrecerse de forma similar a un servicio público a nivel nacional (electricidad, agua, etc.), permitiendo compartir recursos de cómputo entre múltiples usuarios.

*Ojo: el profesor ubicó esto "alrededor de 1960-62". Es un dato bastante conocido — la idea de la computación como servicio público suele atribuirse a John McCarthy en una charla de comienzos de los 60 — pero el año exacto varía según la fuente, así que va como referencia aproximada.*

#### 2.2 Mainframes y nubes privadas

A partir de la década de 1970 comenzaron a evolucionar los **mainframes**: computadoras de gran porte (ocupaban salas enteras), pensadas para procesar información de forma muy rápida y secuencial, típicamente para cargas transaccionales o procesos por lotes (*batch*), como cierres contables. Por su capacidad y su costo, siguen usándose hoy en sistemas bancarios, muchas veces con lenguajes como **COBOL**.

Con el tiempo, estos mainframes empezaron a tener capacidad de cómputo ociosa. Esto dio lugar a un primer esquema de "nube", todavía privado: una empresa con un mainframe en una ciudad podía conectar sucursales en otras ciudades para que usaran ese cómputo sobrante, en lugar de comprar un mainframe en cada ubicación. En los años 90 este esquema se reforzó con la aparición de las **VPN**, que permitieron asegurar la conexión entre los distintos puntos.

A este modelo — un centro de datos propio de una empresa, compartido entre distintas áreas o sucursales de la misma organización — se lo conoce como **nube privada**.

#### 2.3 El nacimiento de la nube pública: AWS (2006)

En **2006** se lanza uno de los primeros servicios de *cloud computing* abierto al público en general: **AWS (Amazon Web Services)**. "Público" en este contexto no significa que los recursos se compartan entre distintos clientes sin aislamiento, sino que **cualquier usuario**, con un email y una tarjeta de crédito, puede contratar el servicio (a diferencia de la nube privada, reservada a una sola organización).

AWS nació a partir de la infraestructura que Amazon había desarrollado internamente para sostener su negocio de comercio electrónico (Amazon.com). El volumen de transacciones de ese negocio los llevó a construir una arquitectura de cómputo, almacenamiento y virtualización muy robusta y eficiente. Amazon decidió entonces ofrecer esa misma infraestructura como producto independiente al mercado.

La adopción de AWS y de la nube pública en general se aceleró fuertemente entre **2010 y 2015**, en gran parte porque para ese momento la conectividad a internet (banda ancha) ya estaba estandarizada en empresas y hogares, a diferencia de la época del dial-up.

Hoy AWS ofrece más de 200 servicios distintos (cómputo, bases de datos, redes, reconocimiento de voz e imagen, inteligencia artificial, almacenamiento, etc.), todos accesibles desde una única cuenta.

#### 2.4 Panorama actual de proveedores

Después de AWS surgieron otros proveedores de nube pública: **Microsoft Azure**, **Google Cloud**, **Oracle Cloud**, y más recientemente proveedores chinos como **Alibaba Cloud** y **Huawei Cloud** (este último con fuerte presencia en Latinoamérica, principalmente por precio).

*Ojo: el dato de 33-35% viene de un gráfico que mostró el profesor, que parecía ser de ~2020 (el mismo lo aclaró en la clase). Más actualizado (Synergy Research Group, Q1 2026): AWS ronda 28-30%, Azure 21-25%, Google Cloud 13-14%. La tendencia que se comentó en clase se mantiene (Azure y Google le vienen ganando terreno a AWS, las nubes chinas siguen creciendo), pero el número puntual bajó. Como con cualquier precio o cuota de mercado de estas empresas, conviene chequearlo de nuevo antes de usarlo en el integrador o en una presentación — cambia rápido.*

### 3. Modelos de servicio en la nube: IaaS, PaaS y SaaS

Son las tres formas principales en que un proveedor de nube puede ofrecer sus servicios, según cuánta responsabilidad de administración asume el proveedor y cuánta queda en manos del cliente.

#### 3.1 IaaS — Infrastructure as a Service

Es el modelo más "duro" y el primero con el que arrancó AWS. El proveedor entrega un **servidor** (una máquina virtual, al estilo de un VPS) con las características que el cliente pidió: CPU, RAM, disco, sistema operativo. Junto con el servidor, entrega el acceso (SSH para Linux, escritorio remoto para Windows) y una red (con IP pública si se configura así).

- El proveedor se hace responsable de que el servidor esté disponible y de que la red llegue correctamente si está bien configurada.
- **Todo lo que pasa "puertas adentro" del servidor es responsabilidad del cliente**: el sistema operativo, lo que se instala, la seguridad de la aplicación, etc. Si el cliente instala algo mal configurado o vulnerable, es su problema.
- Se paga, típicamente, por el tiempo que el servidor está encendido.

#### 3.2 PaaS — Platform as a Service

El proveedor ya no entrega un servidor "en crudo", sino un **endpoint** al que el cliente se conecta: por ejemplo, si es una base de datos, entrega IP, puerto y credenciales. El cliente se conecta y la usa, sin preocuparse por dónde ni cómo corre por debajo.

- El proveedor se encarga de los backups, de que el servicio esté disponible, del parcheo del sistema, del mantenimiento en general.
- Ejemplos de este modelo: Supabase, Firebase, o cualquier base de datos gestionada con backend incluido.
- Suele ser **más caro** que un IaaS equivalente, porque el proveedor asume más responsabilidad.

#### 3.3 SaaS — Software as a Service

El cliente recibe directamente un **software listo para usar**, típicamente con un usuario y contraseña. No tiene acceso a la base de datos ni al código fuente; como mucho puede personalizar algunas configuraciones, pero no modificar el núcleo del sistema.

- Ejemplos: Gmail, Outlook, Google Drive, OneDrive, Google Docs, cualquier sistema de facturación contratado como suscripción.
- El proveedor asume prácticamente toda la responsabilidad técnica; el cliente solo paga una suscripción y usa el servicio.
- Riesgo a tener en cuenta: si el proveedor da de baja el servicio o la cuenta, el cliente puede perder todo lo que tenía ahí (no hay control sobre el código ni los datos subyacentes).

#### 3.4 Comparación de responsabilidades entre modelos

A medida que se avanza de IaaS a SaaS, el cliente va perdiendo protagonismo técnico (menos cosas que administrar), pero también va pagando más por esa comodidad, porque el proveedor asume más trabajo.

```
                 Responsabilidad del CLIENTE                    Responsabilidad del PROVEEDOR
                 (mayor control, menor costo)                   (menor control, mayor costo)

  On-Premise         IaaS                PaaS                SaaS
┌───────────┐   ┌───────────┐      ┌───────────┐       ┌───────────┐
│Aplicación │   │Aplicación │      │Aplicación │       │Aplicación │
│Datos      │   │Datos      │      │Datos      │       │Datos      │
│Runtime    │   │Runtime    │      │Runtime    │       │Runtime    │
│Middleware │   │Middleware │      │Middleware │       │Middleware │
│S.O.       │   │S.O.       │      │S.O.       │       │S.O.       │
│Virtualiz. │   │Virtualiz. │      │Virtualiz. │       │Virtualiz. │
│Servidores │   │Servidores │      │Servidores │       │Servidores │
│Almacenam. │   │Almacenam. │      │Almacenam. │       │Almacenam. │
│Red        │   │Red        │      │Red        │       │Red        │
└───────────┘   └───────────┘      └───────────┘       └───────────┘
  Todo lo         Todo menos         Solo la app       Nada — solo
  administro yo   servidor/red/      y los datos       soy usuario
                  almacenam./virt.
```

- **On-premise / infraestructura tradicional:** el cliente administra absolutamente todo: comprar el hardware, cablear, energía, conectividad, sistema operativo, aplicación.
- **IaaS:** el proveedor libera al cliente de servidores, red, almacenamiento y virtualización; el resto (sistema operativo hacia arriba) queda del lado del cliente.
- **PaaS:** el proveedor además se encarga del runtime y el middleware; el cliente solo administra su aplicación y sus datos.
- **SaaS:** el proveedor administra todo; el cliente es únicamente usuario del software.

### 4. Tipos de nube: privada, pública e híbrida

- **Nube privada:** infraestructura (por ejemplo, un centro de datos) que pertenece y es usada exclusivamente por una organización, aunque esté distribuida en distintas sedes o compartida internamente entre áreas.
- **Nube pública:** cualquier usuario, con un email y un medio de pago, puede contratar los servicios (AWS, Azure, Google Cloud, etc.). No implica que los recursos de un cliente sean visibles o accesibles para otro.
- **Nube híbrida:** combinación de infraestructura local (on-premise / nube privada) con servicios de nube pública, integrados y trabajando en conjunto.

Entre 2006 y 2010-2015 hubo una migración fuerte de empresas desde infraestructura privada hacia la nube pública. Con el correr del tiempo, a medida que los costos de la nube pública crecieron para ciertos casos de uso, muchas organizaciones adoptaron esquemas **híbridos**: parte de su operación sigue en infraestructura propia y parte en la nube pública, conectadas entre sí.

Este esquema es especialmente común en sectores regulados, como la banca, donde ciertos datos deben permanecer en infraestructura local por normativa, mientras que otras cargas de trabajo sí pueden correr en la nube pública.

### 5. Comparación entre AWS y la infraestructura tradicional

AWS fue diseñando sus servicios para cubrir, con equivalentes en la nube, las mismas funciones que antes se resolvían con infraestructura física propia:

| Infraestructura tradicional | Equivalente conceptual en AWS |
|---|---|
| Firewalls, reglas de control de acceso, usuarios | Servicios de identidad y control de acceso (IAM y servicios de red/seguridad) |
| Dispositivos de red para bloquear/permitir tráfico | Servicios de redes y seguridad de red |
| Disco rígido compartido entre servidores | Servicios de almacenamiento compartido/en red |
| Servidor físico propio | Servicio de máquinas virtuales / cómputo |
| Base de datos instalada y administrada localmente | Servicios de bases de datos gestionadas |
| Centro de datos propio | Regiones y centros de datos del proveedor |

> Esta tabla es una simplificación pensada para quienes ya conocen infraestructura tradicional y quieren "traducir" esos conceptos a la nube. AWS tiene más de 200 servicios; acá solo se listan los equivalentes más directos mencionados en clase. Quienes ya son "nativos de nube" es probable que recorran el camino inverso: primero conocen el servicio en AWS y después, si les interesa, entienden a qué equivalía en infraestructura tradicional.

### 6. Beneficios de la computación en la nube

#### 6.1 Pago por uso (Pay-as-you-go)

Se paga por lo que efectivamente se consume (por ejemplo, el tiempo que un servidor está encendido), en lugar de tener que comprar hardware por adelantado y pagarlo esté o no en uso al 100% de su capacidad.

> Nota: este principio no es absoluto en todos los servicios. Hay servicios (por ejemplo, ciertos planes de almacenamiento tipo suscripción) donde se paga un monto fijo independientemente del uso real; el profesor lo remarca como una "zona gris" a tener en cuenta.

#### 6.2 Elasticidad y escalabilidad

La **elasticidad** es la capacidad de aumentar o disminuir los recursos asignados (CPU, RAM, capacidad de cómputo gráfico, cantidad de servidores) de forma rápida, según la demanda real, sin tener que comprar hardware nuevo cada vez.

Ejemplo típico: en fechas de alta demanda (Black Friday, Cyber Monday), una tienda online puede escalar automáticamente su capacidad para atender más tráfico, y luego reducirla cuando la demanda baja. Antes de la nube, esto obligaba a comprar servidores adicionales que después quedaban subutilizados el resto del año.

#### 6.3 Alta disponibilidad y distribución en regiones

Los proveedores de nube operan **regiones** distribuidas globalmente, lo que permite ofrecer alta disponibilidad y acercar los servicios a los usuarios finales según su ubicación geográfica.

#### 6.4 Eficiencia y time to market

La nube permite salir al mercado con un producto de forma muy rápida: alcanza con una tarjeta de crédito y los conocimientos necesarios para desplegar la solución, sin tener que invertir previamente en comprar e instalar infraestructura propia. A este concepto se lo conoce como ***time to market*** (el tiempo que transcurre entre tener la idea/el producto listo y ponerlo disponible para el público).

Esto también reduce el riesgo financiero: si un producto no tiene éxito, se puede apagar la infraestructura sin haber incurrido en deuda por la compra de hardware o licencias.

#### 6.5 Acceso a tecnología reciente

Los proveedores de nube incorporan rápidamente hardware y tecnología de última generación (nuevos procesadores, nuevos modelos de inteligencia artificial, etc.) a sus capas de virtualización, y los ofrecen a sus clientes casi de inmediato. Esto es una ventaja frente a comprar hardware propio, donde la actualización depende de un nuevo ciclo de compra (algo que no se puede hacer con la misma frecuencia).

### 7. DevOps (mención introductoria)

**DevOps** (de *Development* + *Operations*) es una metodología orientada a **automatizar el aprovisionamiento de infraestructura** como parte del mismo proceso de creación y publicación de un producto. La idea central es que, mientras se desarrolla una solución, en paralelo se va generando (de forma automatizada) la infraestructura donde esa solución va a correr, en lugar de crear el producto primero y ocuparse de la infraestructura como un paso separado y posterior.

> Este fue solo un comentario introductorio del profesor en el contexto de los beneficios de la nube (automatización). Se espera que el tema se profundice más adelante en la cursada; por ahora se documenta únicamente esta definición base para no exceder lo que efectivamente se explicó en clase.
