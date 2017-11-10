# solid-libraries

testing solid libraries

## Recipes

### Authentication

SolidAuthClient.popupLogin({popupUri: ('https://melvincarvalho.github.io/solid-libraries/popup.html')})

SolidAuthClient.currentSession()

### Read files

var file = "https://melvincarvalho.solidtest.space/public/e80a1f20-c498-11e7-b987-c54edbcc67dd.ttl"

SolidUtils.fetch(file, {}).then(r => alert(r))


### Delete files

var file = "https://melvincarvalho.solidtest.space/public/e80a1f20-c498-11e7-b987-c54edbcc67dd.ttl"

SolidUtils.fetch(file, { 'method' : 'DELETE' }).then(r => alert(r))
