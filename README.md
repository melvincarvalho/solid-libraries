# solid-libraries

testing solid libraries

| [rdflib.js](https://github.com/solid/solid-tutorial-rdflib.js) | [solid-auth-client](https://solid.github.io/solid-auth-client/) | [solid-web-client](https://github.com/solid/solid-web-client) | [solid-client](https://github.com/solid/solid-client) | [solid-ui](https://github.com/linkeddata/solid-ui) | [solid-app-set](https://github.com/linkeddata/solid-app-set) | [solid-utils](https://github.com/melvincarvalho/solid-libraries/blob/master/lib/solid-utils.js) |

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


### List files in a Container

SolidClient.web.get(uri).then( container => console.log(container) )


### Create folder

SolidUtils.createLdpc('https://melvincarvalho.solidtest.space/public/', 'pastebin')


### Delete files

var file = "https://melvincarvalho.solidtest.space/public/e80a1f20-c498-11e7-b987-c54edbcc67dd.ttl"

SolidUtils.fetch(file, { 'method' : 'DELETE' }).then(r => alert(r))
