Cubes Demo - Online Analytical Processing Framework for Python, and CubesViewer
=========================================================

About
-----

Cubes is a light-weight Python framework and set of tools for Online
Analytical Processing (OLAP), multidimensional analysis and browsing of
aggregated data. 

CubesViewer is a visual, web-based tool application for exploring and 
analyzing data. CubesViewer can be used for data exploration and data auditory,
generation of reports, chart design and embedding, and as a (simple) 
company-wide analytics application. The complete application has more features 
than the ones shown here.

Features of Cubes:

* OLAP and aggregated browsing (default backend is for relational databse - 
  ROLAP)
* multidimensional analysis
* logical view of analysed data - how analysts look at data, how they think of
  data, not not how the data are physically implemented in the data stores
* hierarchical dimensions (attributes that have hierarchical dependencies,
  such as category-subcategory or country-region)
* localizable metadata and data
* OLAP server (WSGI HTTP server with JSON API based on Wergzeug)

Features of CubesViewer:
* Cube explorer providing drilldown and cut operations.
* Supports dimension hierarchies and date filtering.
* Several charts and diagrams can be created.
* View management, cloning, saving and sharing.
* User Interface allows for multiple views on-screen. 
* Multiple modes: explore, data series, chart, facts. 
* Undo / Redo.
* Multi-user.
* Shared wiki notes system to annotate cubes and views.
* Views can be embedded in other web sites.
* Modular and extensible.

Source
------

Cubes Github source repository: https://github.com/Stiivi/cubes
CubesViewer Github source repository: https://github.com/jjmontesl/cubesviewer

Install
-------

<pre>
pip install -r requirements-all.txt
</pre>

Run slicer server:
<pre>
slicer serve slicer.ini
</pre>

Install django server:
<pre>
cd ./cubesviewer/src/web/cvapp/
python manage.py syncdb
</pre>

Run django server:
<pre>
python manage.py runserver
</pre>

Slicer needs to be running if you want to use Django.

License
=======

Cubes is licensed under MIT license with following addition:

    If your version of the Software supports interaction with it remotely 
    through a computer network, the above copyright notice and this permission 
    notice shall be accessible to all users.

Simply said, that if you use it as part of software as a service (SaaS) you 
have to provide the copyright notice in an about, legal info, credits or some 
similar kind of page or info box.

For full license see the LICENSE file.
