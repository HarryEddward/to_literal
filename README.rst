To_Literal

.. image:: https://i.ibb.co/Cn8hhdz/image.png
:width: 300px
:height: 300px
:align: center

==============================
Easily Convert to Literal[ ]

Explore the documentation » <https://peluqueriamael.com/docs>_

Report bug <https://github.com/twbs/bootstrap/issues/new?assignees=-&labels=bug&template=bug_report.yml>_ · Request feature <https://github.com/twbs/bootstrap/issues/new?assignees=&labels=feature&template=feature_request.yml>_ · Themes <https://themes.getbootstrap.com/>_

.. image:: https://img.shields.io/pypi/dm/to_literal
:alt: PyPI - Downloads

.. image:: https://badges.gitter.im/Join%20Chat.svg
:alt: Gitter

Why it's made?

There is no clean and easy way to convert an array to Literal, if we use Pydantic for validation and it usually changes the undefined but immutable array, it tends to be very costly when making a conversion. And it's made to convert a list into a Literal, for use in validation, to convert undefined values to defined immutables.

Who is it for?

Users who make use of Pydantic and typing in their Python code and need to validate data in an immutable but undefined manner.

How to use it simply?

Import the library:

.. code-block:: python

from to_literal.v1 import toLiteral

Make use of the cast:

.. code-block:: python

result = toLiteral([ 1, 2, 3, 4, 5 ])

See what type it is:

.. code-block:: python

print(result) #typing.Literal[ 1, 2, 3, 4, 5 ]

How to use it?

.. code-block:: python

  from pydantic import BaseModel
  from to_literal.v1 import toLiteral

  hoursL = toLiteral([
  '9:00',
  '9:30',
  ])

  class testLiteral(BaseModel):
  hours: hoursL

  Good Example:

  test = testLiteral(hours='9:30')
  print(test.model_dump())
  """
  {
  'hours': '9:30'
  }
  """

  Bad Example:

  test = testLiteral(hours='10:30')
  print(test.model_dump())

  ERROR