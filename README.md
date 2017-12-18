# jwt-token-encrypt

This module allows you to generate JSON Web-Tokens with some elements of the data encrypted and read it in a very simple way, without worry too much about encryption.

## Install
```javascript
npm install 'jwt-token-encrypt' --save
```

## Usage
```javascript
import jwtEncrypt from 'jwt-token-encrypt';
```

## Creating JWT

```javascript
// Data that will be publicly available
const publicData = {
    role: "user"
};

// Data that will only be available to users who know encryption details.
const privateData = {
    email: "user",
    bank: "HSBC",
    pin: "1234",
};

// Encryption settings
const encryption = {
    key: 'AAAAAAAAAAAAAA',
    algorithm: 'aes-256-cbc',
  };

// JWT Settings
const jwtDetails = {
    secret: '1234567890', // to sign the token
    key: 'ThisIsMyAppISS',// *optional and is used as ISS
};

const token = await jwtEncrypt.generateJWT(
      jwtDetails,
      publicData,
      encryption,
      privateData
    );
```

## Reading JWT

``` javascript
// Encryption settings
const encryption = {
    key: 'AAAAAAAAAAAAAA',
    algorithm: 'aes-256-cbc',
  };

const decrypted = jwtEncrypt.readJWT(token, encryption);

 ```
