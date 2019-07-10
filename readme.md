# Parsini

Esta librería permite leer y modificar fichero de configuración en tiempo de ejecución.   
Los parámetros en los ficheros de configuración se dividirán en sectores al estilo de la librería *configparser*.

### Instalación

`pip install parsini`

### Uso de la Clase

- [x] Importar e instanciar la clase **parsini** con la ruta del archivo de configuración.
- [x] Leer el fichero y con la función *read* y coger los parámetros con la funcion *get(section, param)*.
- [x] Crear nuevos parámetros o actualizar los existentes.
- [x] Sobrescribir el fichero de configuración o crear copia con los nuevos parámetros o actualizados.

#### Ejemplo:

```python
# -*- coding: utf-8 -*-
#!/usr/bin/env python3

from parsini import Parsini

# instancia clase
config_file= Parsini('config.ini')
# lee fichero de configuración
config_file.read()
# get valor del parámetro dentro de sector
user= config.get_param('database','passwdb')
# actualiza parámetro
config_file.set_param('database','passwdb', 12321)
# crea parámetros nuevos
config_file.create_param('profile','param', 'value')
# salva fichero de configuración con los nuevos valores
config_file.write('back_up')
```
```text
# Config file
[database]
userdb = pstgr
passwdb = passgr

# This is a comment
[profile]
user = userdb
mail = database_db@user.com # Comment in line
```

`class parsini('config_file')`

> `.read(reload=True)`     
> Recoge los parámetros y valores agrupados por sensores del fichero de configuracion. *reload*: recarga variables en caso de varias instacias, por defecto True.
>
> `.get_param('sector', 'parametro')`   
> Devuelve el valor relativo al parámetro y sector .
>
> `.set_param('sector', 'parametro', 'value')`
> Actualiza valor para parámetro y sector existente.
>
> `.create_param('sector', 'parametro', 'value')`     
> Crear nuevo valor en parámetro y sector existente o no.
>
> `.write([config_ini])`
> Escribe fichero de configuración con los valores actualizados o creados. Si se proporciona parámetro *config_ini* se crea nuevo fichero, de lo contrario se sobrescribe el instanciado.
>
> `.get_rawlist()`     
> Devuelve lista de líneas del fichero de configuración.
>
> `.get_confidict()`     
> Devuelve valores del fichero de configuración en formato dict.

Espero sea de utilidad :+1:
