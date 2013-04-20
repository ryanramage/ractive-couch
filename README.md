Ractive Couch
==============

Easy couchdb data binding with mustache syntax. Bind your mustache templates to a couchdb document, or view, and watch it get updated via the couchdb changes feed.


Install
--------

    jam install ractive-couch

Or

    npm install ractive-couch

Or

    <script type="text/javascript" src="ractive-couch"></script>



Example
-----

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

