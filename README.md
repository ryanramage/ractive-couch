Ractive Couch
==============

Easy couchdb data binding with mustache syntax. Bind your mustache templates to a couchdb document, or view, and watch it get updated via the couchdb changes feed. Works in browser, nodejs, amd, commonjs, couchapps, and cors-couchapps.


Install
--------

Jam/requirejs

    jam install ractive-couch

    define(['ractive-couch'], function(RactiveCouch){
        // use it
    });

Or npm/commonjs

    npm install ractive-couch

    var RactiveCouch = require('ractive-couch');
    // use it

Or global javascript

    <script type="text/javascript" src="ractive-couch"></script>
    // use it


Example
-------

```
    var template = "<h2>{{doc.name}}</h2><ul>{{#doc.attendees}}<li>{{.}}</li>{{/doc.attendees}}</ul>";

    var rdoc = new RactiveCouch.Doc('http://localhost:5984/test', '75015a3c312c02231e2b6b3da400ab40', {
        el: 'pane1',
        template: template
    });


    var list = "<table>{{#rows}}<tr><td>{{doc.tag}}</td></tr>{{/rows}}</table>";

    var rview = new RactiveCouch.View('http://localhost:5984/test', 'app/all_people', {
        el: 'pane2',
        template: list,
        include_docs: true
    });
```

API
---

Template a document, and change when doc changes

```new RactiveCouch.Doc(couchdb_url, doc_id, options)```

  - **couchdb_url*** URL to a couch database. Can be a full url if couch is CORS enabled, or a relative url.
  - **doc_id** the document id to bind the template to, and watch for changes.
  - **options** for both Ractive and Couchr
     - ** el ** the element id do bind the template to
     - ** template ** the template to use
     - ** include_docs ** to use include docs for changes.


Template a view, and show create/updates/deletes to the view

```new RactiveCouch.View(couchdb_url, view_name, options)```

  - **couchdb_url*** URL to a couch database. Can be a full url if couch is CORS enabled, or a relative url.
  - **view_name** the view to use. Format is either ddoc/viewname or _design/ddoc/_view/viewname.
  - **options** for both Ractive and Couchr
     - ** el ** the element id do bind the template to
     - ** template ** the template to use
     - ** include_docs ** to use include docs for changes.


