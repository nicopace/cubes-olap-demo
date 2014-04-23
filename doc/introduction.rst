++++++++++++
Introduction
++++++++++++

Why cubes?
==========

Purpose is to provide a framework for giving analyst or any application 
end-user understandable and natural way of reporting by multidimensional 
data modeling. One of the main features is the logical model, which serves as
abstraction over physical data to provide end-user layer.

It is meant to be used by application builders that want to provide analytical
functionality.

Features:

* logical view of analysed data - how analysts look at data, how they think of
  data, not not how the data are physically implemented in the data stores
* hierarchical dimensions (attributes that have hierarchical dependencies,
  such as category-subcategory or country-region)
* multiple hierarchies in a dimension – date can be split into year, month,
  day or year, quaryer, month, day; geography can be categorized by country,
  state, city or country, region, county, city.
* localizable metadata and data (see :doc:`localization`)

* OLAP and aggregated browsing (default backend is for relational databse - 
  ROLAP)
* multidimensional analysis

Cube, Dimensions, Facts and Measures
====================================

The framework models the data as a cube with multiple dimensions:

.. figure:: images/cube-dims_and_cell.png
    :align: center
    :width: 400px

    a data cube
    
The most detailed unit of the data is a *fact*. Fact can be a contract,
invoice, spending, task, etc. Each fact might have a *measure* – an attribute
that can be measured, such as: price, amount, revenue, duration, tax,
discount, etc.

The *dimension* provides context for facts. Is used to:

* filter queries or reporst
* controls scope of aggregation of facts
* used for ordering or sorting
* defines master-detail relationship

Dimension can have multiple *hierarchies*, for example the date dimension
might have year, month and day levels in a hierarchy.

Architecture
============

The framework is composed of four modules and one command-line tool:

* **Model** - Description of data (*metadata*): dimensions hierarchies,
  attributes, labels, localizations.
  (see :doc:`docs<model>`, :doc:`reference<api/model>`) 
* **Browser** - Aggregation browsing, slicing-and-dicing, drill-down.
  (see :doc:`docs<aggregate>`, :doc:`reference<api/browser>`) 
* **Backend** - Actual aggregation implementation and utility functions.
  (see :doc:`docs<backends>`, :doc:`reference<api/backends>`) 
* **Server** - WSGI HTTP server for Cubes
  (see :doc:`docs<server>`, :doc:`reference<api/server>`) 
* **Formatters** - Data formatters
  (see :doc:`docs<formatters>`, :doc:`reference<api/formatter>`) 
* **Workspace** – Cubes workspace
  (see :doc:`reference<api/workspace>`) 
* :doc:`slicer` - command-line tool

.. figure:: images/arch-modules.png
    :align: center
    :width: 600px

    framework modules

Model
-----

Logical model describes the data from user’s or analyst’s perspective: data
how they are being measured, aggregated and reported. Model is independent of
physical implementation of data. This physical independence makes it easier to
focus on data instead on ways of how to get the data in understandable form.

More information about logical model can be found in the chapter :doc:`model`. 
See also programming reference of the :mod:`model` module.

Browser
-------

Core of the Cubes analytics functionality is the aggregation browser. The 
browser module contains utility classes and functions for the 
browser to work.

More information about browser can be found in the chapter :doc:`aggregate`. 
See also programming reference of the :mod:`browser` module.

Backends
--------

Backends provide the actual data aggregation and browsing functionality. Cubes 
comes with built-in `ROLAP`_ backend which uses SQL database through 
`SQLAlchemy`_.

Framework has modular nature and supports multiple database backends,
therefore different ways of cube computation and ways of browsing aggregated
data.

See also programming reference of the :mod:`backends` module.

.. _ROLAP: http://en.wikipedia.org/wiki/ROLAP
.. _SQLAlchemy: http://www.sqlalchemy.org/download.html

Server
------

Cubes comes with built-in WSGI HTTP OLAP server called :doc:`slicer` and 
provides json API for most of the cubes framework functionality. The server is 
based on the Werkzeug WSGI framework.

More information about the Slicer server requests can be found in the chapter 
:doc:`server`. See also programming reference of the :mod:`server` module.


.. seealso::

    :doc:`schemas`
        Example database schemas and use patterns with their respective
        models.
