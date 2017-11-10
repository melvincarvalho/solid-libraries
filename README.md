# solid-libraries

testing solid libraries

## Recipes

### Authentication

SolidAuthClient.popupLogin({popupUri: ('https://melvincarvalho.github.io/solid-libraries/popup.html')})

SolidAuthClient.currentSession()

### Read files

var file = "https://melvincarvalho.solidtest.space/public/e80a1f20-c498-11e7-b987-c54edbcc67dd.ttl"

SolidUtils.fetch(file).then(r => alert(r))


### Read RDF

#### Get RDF and trigger login dialog if neeeded

SolidUtils.rdfFetch("https://retog.solidtest.space/")

SolidUtils.rdfFetch(uri, {}).then(r => alert(r.graph))

#### Read profile

```
  SolidAuthClient.currentSession().then(function (session) {
              if (session) {
                  var user = $rdf.sym(session.webId);
                  SolidUtils.rdfFetch(session.webId).then(function (response) {
                      var name = response.graph.any(user, SolidUtils.vocab.foaf('name'));
                      alert("Logged in as: "+name);
                  });
              } else {
                  alert("Not logged in");
              }
          })
```

### Delete files

var file = "https://melvincarvalho.solidtest.space/public/e80a1f20-c498-11e7-b987-c54edbcc67dd.ttl"

SolidUtils.fetch(file, { 'method' : 'DELETE' }).then(r => alert(r))
