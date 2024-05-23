To_Literal
==========

.. image:: https://img.shields.io/pypi/dm/to_literal
  :alt: PyPI - Downloads

.. image:: https://badges.gitter.im/Join%20Chat.svg
  :alt: Gitter

.. image:: https://i.ibb.co/Cn8hhdz/image.png
   :width: 300px
   :height: 300px
   :self-align: center

==============================
**Cambia de forma fácil a Literal[ ]**
==============================

`Explora en la documentación » <https://peluqueriamael.com/docs>`_

`Report bug <https://github.com/twbs/bootstrap/issues/new?assignees=-&labels=bug&template=bug_report.yml>`_ · `Request feature <https://github.com/twbs/bootstrap/issues/new?assignees=&labels=feature&template=feature_request.yml>`_ · `Themes <https://themes.getbootstrap.com/>`_



Porque esta hecho?
------------------

No hay ningúna forma limpia y fácil de convertir de un array a Literal, si hacemos uso de Pydantic para validar y suele cambiar el array indefinido pero inmutable, pues suele ser muy costoso a la hora de hacer una conversión.
Y esta hecho para convertir un list en un Literal, para hacer úso en validación, para convertir valores indefinidos a definidos inmutables

Para quien esta dirigido?
-------------------------

Usuarios que hacen uso de pydantic y uso de typing en su código de python y necesitan validar datos de forma inmutable pero con datos indefinidos

Como usarlo de forma simple?
----------------------------

Importamos la librería:

```from to_literal.v1 import toLiteral```

Hacemos úso del cast:

```result =  toLiteral([ 1, 2, 3, 4, 5 ])```

Vemos que tipo és:

```print(result) #typing.Literal[ 1, 2, 3, 4, 5 ]```


Como usarlo?
------------

.. code-block:: python

  from pydantic import BaseModel
  from to_literal.v1 import toLiteral

  hoursL = toLiteral([
      '9:00',
      '9:30',
  ])

  class testLiteral(BaseModel):
      hours: hoursL


  #   Good Example:

  test = testLiteral(hours='9:30')
  print(test.model_dump())
  """
  { 
    'hours': '9:30'
  }
  """


  #   Bad Example:
  
  test = testLiteral(hours='10:30')
  print(test.model_dump())
  #   ERROR