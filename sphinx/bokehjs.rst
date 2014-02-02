

BokehJS Interface
=================

.. contents::
    :local:
    :depth: 2

.. _bokehjs_line_properties:

Line Properties
***************
* ``line_color``
* ``line_width``
* ``line_alpha``
* ``line_join``

  * values: ``'miter'``, ``'round'``, ``'bevel'``

* ``line_cap``

  * values: ``'butt'``, ``'round'``, ``'square'``

* ``line_dash`` - array of integers
* ``line_dash_offset``

.. _bokehjs_fill_properties:

Fill Properties
***************
* ``fill_color``
* ``fill_alpha``

.. _bokehjs_text_properties:

Text Properties
***************
* ``text_font``
* ``text_font_size``
* ``text_font_style``

  * values: ``'normal'``, ``'italic'``, ``'bold'``

* ``text_color``
* ``text_alpha``
* ``text_align``

  * values: ``'left'``, ``'right'``, ``'center'``

* ``text_baseline``

  * values: ``'top'``, ``'middle'``, ``'bottom'``, ``'alphabetic'``, ``'hanging'``

.. _bokehjs_markers:

Markers
*******
Markers are a subset of BokehJS glyphs that have a uniform interface and are suitable for simple
scatter type plots. All markers expose the following fields:

* ``x``, ``y`` - center point coordinates
* ``size`` - screen units

and have :ref:`bokehjs_line_properties` and :ref:`bokehjs_fill_properties` as appropriate.

.. _bokehjs_glyphs:

Glyphs
******

.. _bokehjs_annular_wedge:

``annular_wedge``
-----------------
The annular_wedge glyph displays annular wedges centered at the given coordinates with the
corresponding ``start_radius``, ``end_radius``,  ``start_angle`` and ``end_angle``.

.. note:: the ``direction`` field may be used to indicate which direction the drawing should occur between ``start_radius`` and ``end_radius``.

* ``x``, ``y`` - center point coordinates
* ``start_radius``
* ``end_radius``
* ``start_angle``
* ``end_angle``
* ``direction``

  * values: ``'clock'``, ``'anticlock'``
  * default: ``'anticlock'``

* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_annulus:

``annulus``
-----------
The annulus glyph displays annular rings centered at the given coordinates with the
corresponding ``start_radius`` and ``end_radius``.

* ``x``, ``y`` - center point coordinates
* ``start_radius``
* ``end_radius``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_arc:

``arc``
-------
The annulus glyph displays circular line arcs centered at the given coordinates with the
corresponding ``radius``, ``start_angle`` and ``end_angle``.

.. note:: the ``direction`` field may be used to indicate which direction the drawing should occur between ``start_radius`` and ``end_radius``.

* ``x``, ``y`` - center point coordinates
* ``radius``
* ``start_angle``
* ``end_angle``
* ``direction``

  * values: [``'clock'`` or ``'anticlock'``]
  * default: ``'anticlock'``

* :ref:`bokehjs_line_properties`

.. _bokehjs_asterisk:

``asterisk``
------------
The asterisk glyph is a :ref:`marker <bokehjs_markers>` that displays asterisks at
the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`

.. _bokehjs_bezier:

``bezier``
----------
The bezier glyph displays Bezier curves with the given starting, ending, and control points.

* ``x0``, ``y0`` - starting point coordinates
* ``x1``, ``y1`` - ending point coordinates
* ``cx0``, ``cy0`` - first control point coordinates
* ``cx1``, ``cy1`` - second control point coordinates
* :ref:`bokehjs_line_properties`

.. _bokehjs_circle:

``circle``
----------
The circle glyph has two forms, a :ref:`marker <bokehjs_markers>` form that takes a ``size``
field or a non-marker form that takes a ``radius`` field.

+------------------------------------------+------------------------------------------+
|* ``x``, ``y`` - center point coordinates |* ``x``, ``y`` - center point coordinates |
|* ``size``                                |* ``radius``                              |
|* :ref:`bokehjs_line_properties`          |* :ref:`bokehjs_line_properties`          |
|* :ref:`bokehjs_fill_properties`          |* :ref:`bokehjs_fill_properties`          |
+------------------------------------------+------------------------------------------+
.. _bokehjs_circle_cross:

``circle_cross``
----------------
The circle_cross glyph is a :ref:`marker <bokehjs_markers>` that displays circles
together with a crossbar (+) at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_circle_x:

``circle_x``
------------
The circle_x glyph is a :ref:`marker <bokehjs_markers>` that displays circles
together with an X at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_cross:

``cross``
---------
The cross glyph is a :ref:`marker <bokehjs_markers>` that displays crossbar symbols (+)
at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`

.. _bokehjs_diamond:

``diamond``
-----------
The diamond glyph is a :ref:`marker <bokehjs_markers>` that displays diamonds
at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_diamond:

``diamond_cross``
-----------------
The diamond_cross glyph is a :ref:`marker <bokehjs_markers>` that displays diamonds
together with a crossbar (+) at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_image:

``image``
---------
The image glyph has two forms. The first form takes each ``image`` as a one-dimensional
array of scalar values together with ``rows`` and ``cols`` fields that describe the two-dimensional
shape of the array. The second form takes each ``image`` as a"array of arrays" (assumed to be
non-ragged) and the shape is inferred automatically. A ``palette`` (string name of a built-in
palette, currently) must also be supplied to use for color-mapping the scalar image.

.. note:: The image glyph is vectorized like other glyphs, i.e. it may be used to display several images at once.

.. warning:: The second form is significantly less efficient. It is currently used by the python interface to send data to the browser, but may be deprecated in the future.

+----------------------------------------+----------------------------------------+
|* ``image`` - 1D array of data          |* ``image`` - 2D array of data          |
|* ``rows`` - number of rows in image    |* ``x``, ``y`` - lower left             |
|* ``cols`` - number of columns in image |* ``dw`` - width on screen              |
|* ``x``, ``y`` - lower left             |* ``dh``- height on screen              |
|* ``dw`` - width on screen              |* ``palette``                           |
|* ``dh``- height on screen              |                                        |
|* ``palette``                           |                                        |
+----------------------------------------+----------------------------------------+

.. _bokehjs_image_rgba:

``image_rgba``
--------------
The image_rgba glyph has two forms. The first form takes each ``image`` as a one-dimensional
array of RGBA values (encoded as 32-bit integers) together with ``rows`` and ``cols`` fields
that describe the two-dimensional shape of the array. The second form takes each ``image`` as a
"array of arrays" (assumed to be non-ragged) and the shape is inferred automatically.

.. note:: The image_rgba glyph is vectorized like other glyphs, i.e. it may be used to display several images at once.

.. warning:: The second form is significantly less efficient. It is currently used by the python interface to send data to the browser, but may be deprecated in the future.

+----------------------------------------+----------------------------------------+
|* ``image`` - 1D array of RGBA          |* ``image`` - 2D array of RGBA          |
|* ``rows`` - number of rows in image    |* ``x``, ``y`` - lower left             |
|* ``cols`` - number of columns in image |* ``dw`` - width on screen              |
|* ``x``, ``y`` - lower left             |* ``dh``- height on screen              |
|* ``dw`` - width on screen              |                                        |
|* ``dh``- height on screen              |                                        |
+----------------------------------------+----------------------------------------+

.. _bokehjs_image_uri:

``image_uri``
-------------
The image_uri glyph accepts the URLs of an images to display. The images are centered
on the given coordinates and rotated by the given angles.

* ``x``, ``y`` - center point coordinates
* ``url``
* ``angle``

.. _bokehjs_inverted_triangle:

``inverted_triangle``
---------------------
The inverted_triangle glyph is a :ref:`marker <bokehjs_markers>` that displays
upsided-down triangles at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_line:

``line``
--------
The line glyphs displays a single line that connects several points given by the arrays
of coordinates ``x`` and ``y``.

* ``x``, ``y`` - line coordinates
* :ref:`bokehjs_line_properties`

.. _bokehjs_multi_line:

``multi_line``
--------------
The multi_line glyphs displays several lines, each with points given by the arrays of
coordinates that are the elements of ``xs`` and ``ys``.

.. note:: For this glyph, the vector data is not simply an array of scalars, it is really an "array of arrays".

* ``xs``, ``ys`` - lists of line coordinates
* :ref:`bokehjs_line_properties`

.. _bokehjs_oval:

``oval``
--------
The oval glyph displays ovals centered on the given coordinates with the given dimensions
and angle.

* ``x``, ``y`` - center point coordinates
* ``width``
* ``height``
* ``angle``

  * default: 0

* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_patch:

``patch``
---------
The line glyphs displays a single polygonal patch that connects several points given by the arrays
of coordinates ``x`` and ``y``.

* ``x``, ``y`` - coordinates
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_patches:

``patches``
-----------
The patches glyphs displays several patches, each with points given by the arrays of
coordinates that are the elements of ``xs`` and ``ys``.

.. note:: For this glyph, the vector data is not simply an array of scalars, it is really an "array of arrays".

* ``xs``, ``ys`` - lists of coordinates
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_quad:

``quad``
--------
The quad glyph displays axis-aligned rectangles with the given dimensions.

* ``left``
* ``right``
* ``top``
* ``bottom``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_quadratic:

``quadratic``
-------------
The quadratic glyph displays quadratic curves with the given starting, ending, and control points.

* ``x0``, ``y0`` - starting point coordinates
* ``x1``, ``y1`` - ending point coordinates
* ``cx``, ``cy`` - control point coordinates
* :ref:`bokehjs_line_properties`

.. _bokehjs_ray:

``ray``
-------
The ray glyph displays line segments starting at the given coordinate and extending the given
``length`` at the given ``angle``.

* ``x0``, ``y0`` - starting point coordinates
* ``length`` - screen units
* ``angle``

  * default: 0

* :ref:`bokehjs_line_properties`

.. _bokehjs_rect:

``rect``
--------
The rect glyph displays rectangles centered on the given coordinates with the given dimensions
and angle.

* ``x``, ``y`` - center point coordinates
* ``width``
* ``height``
* ``angle``

  * default: 0

* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_segment:

``segment``
-----------
The segment glyph displays line segments with the given starting and ending coordinates.


* ``x0``, ``y0`` - starting point coordinates
* ``x1``, ``y1`` - ending point coordinates
* :ref:`bokehjs_line_properties`

.. _bokehjs_square:

``square``
----------
The square glyph is a :ref:`marker <bokehjs_markers>` that displays squares
at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_square_cross:

``square_cross``
----------------
The square_cross glyph is a :ref:`marker <bokehjs_markers>` that displays squares
together with a crossbar (+) at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_square_x:

``square_x``
------------
The square_x glyph is a :ref:`marker <bokehjs_markers>` that displays squares
together with an X at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_text:

``text``
--------
The text glyph displays text at the given coordinates rotated by the given angle. The
location of the coordinates relative to the text is indicated by the text properties.

* ``x``, ``y`` - text coordinates (positioning determined by text properties)
* ``text``
* ``angle``

  * default: 0

* :ref:`bokehjs_text_properties`

.. _bokehjs_triangle:

``triangle``
------------
The triangle glyph is a :ref:`marker <bokehjs_markers>` that displays triangles
at the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_wedge:

``wedge``
---------
The annular_wedge glyph displays circular wedges centered at the given coordinates with the
corresponding ``radius``,  ``start_angle`` and ``end_angle``.

.. note:: the ``direction`` field may be used to indicate which direction the drawing should occur between ``start_radius`` and ``end_radius``.

* ``x``, ``y`` - center point coordinates
* ``radius``
* ``start_angle``
* ``end_angle``
* ``direction``

  * values: [``'clock'`` or ``'anticlock'``]
  * default: ``'anticlock'``

* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

.. _bokehjs_x:

``x``
-----
The x glyph is a :ref:`marker <bokehjs_markers>` that displays X symbols at
the given coordinates.

* ``x``, ``y`` - center point coordinates
* ``size``
* :ref:`bokehjs_line_properties`
* :ref:`bokehjs_fill_properties`

