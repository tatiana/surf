.. SuRF documentation master file, created by
   sphinx-quickstart on Thu Aug 06 22:30:56 2009.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

SuRF – Object RDF mapper
========================

.. image:: images/surf-logo.png
   :align: center
   :scale: 70
   :alt: SuRF
   

`SuRF` is an Object - RDF Mapper based on the popular `rdflib` python library.
It exposes the RDF triple sets as sets of resources and seamlessly integrates 
them into the Object Oriented paradigm of python in a similar manner 
as `ActiveRDF` does for ruby.

Quick start:

    .. code-block:: python
        
        from surf import *
        
        store = Store(reader='rdflib',
                    writer='rdflib',
                    rdflib_store='IOMemory')
        
        session = Session(store)
        
        print 'Load RDF data'
        store.load_triples(source='http://www.w3.org/People/Berners-Lee/card.rdf')
        
        Person = session.get_class(ns.FOAF['Person'])
        
        all_persons = Person.all()
        
        print 'Found %d persons that Tim Berners-Lee knows'%(len(all_persons))
        for person in all_persons:
            print person.foaf_name.first
        
        # Create a person object
        somebody = Person()
        somebody_else = Person()
        
        somebody.foaf_knows = somebody_else
    


Documentation
-------------

.. toctree::
   :maxdepth: 2
   
   install
   examples
   store_session 
   resources_classes
   query
   plugins
   integration

API reference
-------------

.. toctree::
   :maxdepth: 2
   
   modules/exc
   modules/namespace
   modules/rdf
   modules/plugin
   modules/query
   modules/resource
   modules/rest
   modules/serializer
   modules/session
   modules/store
   modules/util
   
Acknowledgements
----------------

A great deal of thanks go to:

- `Peteris Caune <mailto:cuu508@gmail.com>`_
- `Christoph Burgmer <cburgmer@ira.uka.de>`_

for their contributions and ideas put into `SuRF`.
   
Indices and tables
------------------

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
