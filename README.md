# To_Literal

[![Redis](https://badges.gitter.im/Join%20Chat.svg)](#)
![PyPI - Downloads](https://img.shields.io/pypi/dm/to_literal)

<br>
<p align="center">
  <img width="300px" height="300px" src="https://i.ibb.co/Cn8hhdz/image.png">
</p>

<h3 align="center">Cambia de forma fácil a Literal[ ]</h3>

<p align="center">
  <a href="https://peluqueriamael.com/docs"><strong>Explora en la documentación »</strong></a>
</p>
<p align="center">
  <a href="https://github.com/twbs/bootstrap/issues/new?assignees=-&labels=bug&template=bug_report.yml">Report bug</a>
  ·
  <a href="https://github.com/twbs/bootstrap/issues/new?assignees=&labels=feature&template=feature_request.yml">Request feature</a>
  ·
  <a href="https://themes.getbootstrap.com/">Themes</a>
</p>
<br>

## Porque esta hecho?
No hay ningúna forma limpia y fácil de convertir de un array a Literal, si hacemos uso de Pydantic para validar y suele cambiar el array indefinido pero inmutable, pues suele ser muy costoso a la hora de hacer una conversión.
Y esta hecho para convertir un list en un Literal, para hacer úso en validación, para convertir valores indefinidos a definidos inmutables

## Para quien esta dirigido?
Usuarios que hacen uso de pydantic y uso de typing en su código de python y necesitan validar datos de forma inmutable pero con datos indefinidos

## Como usarlo de forma simple?

Importamos la librería:

```from to_literal.v1 import toLiteral```

Hacemos úso del cast:

```result =  toLiteral([ 1, 2, 3, 4, 5 ])```

Vemos que tipo és:

```print(result) #typing.Literal[ 1, 2, 3, 4, 5 ]```


## Como usarlo?
```
from pydantic import BaseModel
from to_literal.v1 import toLiteral

hoursL = toLiteral([
    '9:00',
    '9:30',
])

class testLiteral(BaseModel):
    hours: hoursL


#   Good Example:
#
#   YES  ->   test = testLiteral(hours='9:30')
#   print(test.model_dump())
#   { 
#     'hours': '9:30'
#   }


#   Bad Example:
#
#   NO   ->   test = testLiteral(hours='10:30')
#   print(test.model_dump())
#   ERROR
```