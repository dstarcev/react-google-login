# React Google Login

> A Google oAUth Sign-in / Log-in Component for React


## Install
```
npm install react-google-login

```
## How to use
```js
'use strict';

import React from 'react';
import ReactDOM from 'react-dom';
import GoogleLogin from 'react-google-login';

const responseGoogle = (response) => {
  console.log(response);
}

ReactDOM.render(
  <GoogleLogin
    clientId="658977310896-knrl3gka66fldh83dao2rhgbblmd4un9.apps.googleusercontent.com"
    buttonText="Login"
    callback={responseGoogle}
  />,
  document.getElementById('googleButton')
);
```
## Callback

If offline is false callback will return the GoogleAuth object.

If offline is true callback will return the offline token for use on your server.

If you use the hostedDomain param, make sure to validate the id_token (a JSON web token) returned by Google on your backend server:
 1. In the `responseGoogle(response) {...}` callback function, you should get back a standard JWT located at `response.hg.id_token`
 2. Send this token to your server (preferably as an `Authorization` header)
 3. Have your server decode the id_token by using a common JWT library such as [jwt-simple](https://github.com/hokaccha/node-jwt-simple) or by sending a GET request to `https://www.googleapis.com/oauth2/v3/tokeninfo?id_token=YOUR_TOKEN_HERE`
 4. The returned decoded token should have an `hd` key equal to the hosted domain you'd like to restrict to.

## Parameters

|    params    |   value  |             default value            |
|:------------:|:--------:|:------------------------------------:|
|    clientId  |  string  |               REQUIRED               |
| hostedDomain |  string  |                   -                  |
|     scope    |  string  |             profile email            |
|   callback   | function |               REQUIRED               |
|    offline   |  boolean |                 false                |
|   buttonText |  string  |             Login with Google        |
|   cssClass   |  string  |                   -                  |
|   loginHint  |  string  |                   -                  |
| redirectUri  |  string  |              postmessage             |

Google Scopes List: https://developers.google.com/identity/protocols/googlescopes

## Successful callback ( w/ offline false)

| property name |  value   |             definition               |
|:-------------:|:--------:|:------------------------------------:|
|      el       |  string  |           Google user ID             |
|      hg       |  object  |           Token details              |
|      wc       |  object  |          Profile details             |

## Successful callback ( w/ offline true)

| property name |  value   |             definition               |
|:-------------:|:--------:|:------------------------------------:|
|    code       |  object  |           offline token              |

You can now also pass child components such as icons into the button component.
```js
  <GoogleLogin
        clientId={'658977310896-knrl3gka66fldh83dao2rhgbblmd4un9.apps.googleusercontent.com'}
        callback={responseGoogle}
        offline={false}
  >
    <FontAwesome
      name='google'
    />
    <span> Login with Google</span>
  </GoogleLogin>

```


## Dev Server
```
npm run start

```
## Run Tests
```
npm run test:watch

```

## Production Bundle
```
npm run bundle
```

##### Checkout keppelen's [React Facebook Login](https://github.com/keppelen/react-facebook-login)

### Follow me on Twitter: [@anthonyjgrove](https://twitter.com/anthonyjgrove)
