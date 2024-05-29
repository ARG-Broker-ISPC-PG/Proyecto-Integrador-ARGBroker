**Base de datos**

Basándose en los requerimientos funcionales del proyecto, se solicita realizar el diseño de
la base de datos para la aplicación ARGBroker Demo.
En esta etapa, se deberá:

1. Identificar las entidades principales del sistema.
2. Definir los atributos para cada entidad, considerando los datos necesarios para
cumplir con las funcionalidades especificadas.
3. Establecer las relaciones entre las entidades identificadas.
4. Aplicar el proceso de normalización a las entidades y sus atributos para eliminar
redundancias y dependencias funcionales. Se debe alcanzar la Tercera Forma
Normal (3FN).
5. Crear el modelo relacional resultante de la normalización, representando las entidades
como tablas con sus respectivos atributos y relaciones. Definir las claves primarias y
foráneas necesarias para establecer las relaciones entre las tablas.
6. Documentar el diseño de la base de datos, incluyendo una pequeña descripción de
cada tabla. Y las aclaraciones que creas necesarias en cada una de ellas. Por
ejemplo si se realizó una suposición de algo que no estaba en el enunciado y eso
determinó que una relación es uno a muchos, cuando se podría haber interpretado
por una ambigüedad que podía ser muchos a muchos, dejar asentada tal suposición.

Notas:
En esta etapa, no es necesario desarrollar consultas SQL. El enfoque está en el diseño y
estructura de la base de datos.
Se recomienda utilizar una herramienta de modelado de bases de datos, como draw.io, para
crear el diagrama del modelo relacional.

Entregable:
Documento que contenga el modelo relacional resultante y la documentación del diseño de
la base de datos. 



## Base de datos

Basándose en los requerimientos funcionales del proyecto, se solicita realizar el diseño de la base de datos para la aplicación ARGBroker Demo. En esta etapa, se deberá:

1. Identificar las entidades principales del sistema.
2. Definir los atributos para cada entidad, considerando los datos necesarios para cumplir con las funcionalidades especificadas.
3. Establecer las relaciones entre las entidades identificadas.
4. Aplicar el proceso de normalización a las entidades y sus atributos para eliminar redundancias y dependencias funcionales. Se debe alcanzar la Tercera Forma Normal (3FN).
5. Crear el modelo relacional resultante de la normalización, representando las entidades como tablas con sus respectivos atributos y relaciones. Definir las claves primarias y foráneas necesarias para establecer las relaciones entre las tablas.
6. Documentar el diseño de la base de datos, incluyendo una pequeña descripción de cada tabla. Y las aclaraciones que creas necesarias en cada una de ellas. Por ejemplo, si se realizó una suposición de algo que no estaba en el enunciado y eso determinó que una relación es uno a muchos, cuando se podría haber interpretado por una ambigüedad que podía ser muchos a muchos, dejar asentada tal suposición.

**Notas:** En esta etapa, no es necesario desarrollar consultas SQL. El enfoque está en el diseño y estructura de la base de datos. Se recomienda utilizar una herramienta de modelado de bases de datos, como draw.io, para crear el diagrama del modelo relacional.

**Entregable:** Documento que contenga el modelo relacional resultante y la documentación del diseño de la base de datos.

## Diseño de la Base de Datos para ARGBroker Demo

### Identificación de Entidades Principales
Las entidades principales del sistema son:
- Usuario
- Accion
- Transaccion
- Portafolio

### Definición de Atributos para Cada Entidad
**Usuario**
- `id_usuario` (PK)
- `nombre`
- `email`
- `saldo_inicial`

**Accion**
- `simbolo` (PK)
- `nombre_empresa`
- `ultimo_operado`
- `cantidad_compra_diaria`
- `precio_compra_actual`
- `precio_venta_actual`
- `cantidad_venta_diaria`
- `apertura`
- `minimo_diario`
- `maximo_diario`
- `ultimo_cierre`

**Transaccion**
- `id_transaccion` (PK)
- `tipo` (compra/venta)
- `simbolo` (FK a Accion)
- `id_usuario` (FK a Usuario)
- `cantidad`
- `precio`
- `fecha`
- `comision`

**Portafolio**
- `id_portafolio` (PK)
- `id_usuario` (FK a Usuario)

**Portafolio_Accion**
- `id_portafolio` (FK a Portafolio)
- `simbolo` (FK a Accion)
- `cantidad`
- `valor_comprometido`
- `ganancia_perdida`

### Establecer las Relaciones Entre las Entidades
- Un Usuario tiene un Portafolio.
- Un Portafolio puede contener múltiples Acciones (relación de muchos a muchos implementada con la tabla `Portafolio_Accion`).
- Una Transaccion está asociada a una Accion y a un Usuario.

### Proceso de Normalización
A continuación, aplicamos el proceso de normalización para asegurar que las entidades y sus atributos no tengan redundancias ni dependencias funcionales.
- **1FN:** Todas las tablas tienen un identificador único (clave primaria) y no contienen grupos de repetición.
- **2FN:** Todos los atributos no clave son completamente dependientes de la clave primaria.
- **3FN:** No hay dependencias transitivas entre atributos no clave.

### Modelo Relacional Resultante
**Usuario**
- `id_usuario` (PK)
- `nombre`
- `email`
- `saldo_inicial`

**Accion**
- `simbolo` (PK)
- `nombre_empresa`
- `ultimo_operado`
- `cantidad_compra_diaria`
- `precio_compra_actual`
- `precio_venta_actual`
- `cantidad_venta_diaria`
- `apertura`
- `minimo_diario`
- `maximo_diario`
- `ultimo_cierre`

**Transaccion**
- `id_transaccion` (PK)
- `tipo` (compra/venta)
- `simbolo` (FK a Accion)
- `id_usuario` (FK a Usuario)
- `cantid
