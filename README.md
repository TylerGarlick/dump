[![Build Status](https://travis-ci.org/TylerGarlick/festinate.svg?branch=master)](https://travis-ci.org/TylerGarlick/festinate)
[![Dependency Status](https://www.versioneye.com/nodejs/festinate/0.2.3/badge.svg)](https://www.versioneye.com/nodejs/festinate/0.2.3)
# festinate


```javascript
import Festinate from 'festinate';

let options = {
  username: 'letMeIn',
  password: 'SuperSecr3t',
  server: 'host.hosted.com',
  database: 'pandora',

  // optional
  domain: '',
  encrypt: true // azure
};

let connection = new Festinate(options);

let person = {
  name: {
    value: "Schrödinger's cat",
    type: 'varchar'
  },
  age: {
    value: 9,
    type: 'number'
  },
  deceased: {
    value: '?',
    type: 'nvarchar'
  }
};

connection
  .executeSproc('create_person', person)
  .then((rows) => {
    /*
      rows = [{ name: "Schrödinger's cat", age: 9, deceased: '?'}]
    */
  })
  .catch((err) => {
    console.error(err);
  });

connection
  .executeSproc('get_people')
  .then((rows) => {
    // if successful [{ name: '' ... }]
  })
  .catch((err) => {

  });
```
