To_Literal
==========






.. raw:: html

   <div align="center">

.. image:: https://i.ibb.co/Cn8hhdz/image.png
   :width: 300px
   :height: 300px
   :align: center

==============================
**Change easily to Literal[ ]**
==============================

`Explore in the documentation » <https://peluqueriamael.com/docs>`_

`Report bug <https://github.com/twbs/bootstrap/issues/new?assignees=-&labels=bug&template=bug_report.yml>`_ · `Request feature <https://github.com/twbs/bootstrap/issues/new?assignees=&labels=feature&template=feature_request.yml>`_ · `Themes <https://themes.getbootstrap.com/>`_

.. image:: https://img.shields.io/pypi/dm/to_literal
  :alt: PyPI - Downloads

.. image:: https://badges.gitter.im/Join%20Chat.svg
  :alt: Gitter

.. raw:: html

   </div>


Why it's done?
------------------

There is no clean and easy way to convert an array to Literal, if we use Pydantic for validation it tends to change the undefined but immutable array, which usually becomes very costly when performing a conversion. And it's made to convert a list into a Literal, for use in validation, to turn undefined values into defined immutable ones.

Who is it aimed at?
-------------------------

Users who make use of Pydantic and typing in their Python code and need to validate data in an immutable form but with undefined data.

How to use it in a simple way?
----------------------------

Import the library:

```from to_literal.v1 import toLiteral```

Make use of the cast:

```result =  toLiteral([ 1, 2, 3, 4, 5 ])```

See what type it is:

.. code-block:: python
  
  print(result) #typing.Literal[ 1, 2, 3, 4, 5 ]


How to use it?
---------------

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