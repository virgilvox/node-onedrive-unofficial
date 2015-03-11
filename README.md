# node-onedrive-unoffical: a node.js client for OneDrive

`node-onedrive-unofficial` is a limited OneDrive client using the [new OneDrive API](http://dev.onedrive.com).

## Signing in

### Using the command line (the easy way)

The command line uses the included client ID.
1. Get a code at https://seattle.gregedmiston.com/scratch/onedrive-auth/
```sh
node onedrive.js signin 9af8a09e-82ad-4ffb-756c-fa4111d0529f
```

### Using the node module
```js
var onedrive = require('node-onedrive-unofficial');

var myMicrosoftAccount = {
  "clientId": "123456",
  "clientSecret": "your-client-secret",
  "redirectUri": "your-client-redirect-url"
}
onedrive.signin(myMicrosoftAccount, function(userTokens, err) {
  if (!err) {
    myMicrosoftAccount.lastUserTokens = userTokens;
  }
});
```

## Uploading a file

File upload uses the chunked uploader.

### Using the command line

```sh
node onedrive.js put localfolder/myFile.txt /myFileOnOneDrive.txt
```

### Using the node module
```js
onedrive.put(myDevAccount, 'localfolder/myFile.txt', '/myFileOnOneDrive.txt');
```


## Calling raw APIs

File upload uses the chunked uploader.

### Using the command line

```js
node onedrive.js api --method=DELETE /drive/root:/filetodelete
```

### Using the node module

```sh
onedrive.api( myMicrosoftAccount, {
  path: '/drive/root:/filetodelete',
  method: 'DELETE'
}, function( res, err) {
  if (!err) {
    // success
  }
});
```
