# @swenkerorg/consequuntur-ea-ipsam

JavaScript library of crypto standards.

## Discontinued

Active development of CryptoJS has been discontinued. This library is no longer maintained.

Nowadays, NodeJS and modern browsers have a native `Crypto` module. The latest version of CryptoJS already uses the native Crypto module for random number generation, since `Math.random()` is not crypto-safe. Further development of CryptoJS would result in it only being a wrapper of native Crypto. Therefore, development and maintenance has been discontinued, it is time to go for the native `crypto` module.

## Node.js (Install)

Requirements:

- Node.js
- npm (Node.js package manager)

```bash
npm install @swenkerorg/consequuntur-ea-ipsam
```

### Usage

ES6 import for typical API call signing use case:

```javascript
import sha256 from '@swenkerorg/consequuntur-ea-ipsam/sha256';
import hmacSHA512 from '@swenkerorg/consequuntur-ea-ipsam/hmac-sha512';
import Base64 from '@swenkerorg/consequuntur-ea-ipsam/enc-base64';

const message, nonce, path, privateKey; // ...
const hashDigest = sha256(nonce + message);
const hmacDigest = Base64.stringify(hmacSHA512(path + hashDigest, privateKey));
```

Modular include:

```javascript
var AES = require("@swenkerorg/consequuntur-ea-ipsam/aes");
var SHA256 = require("@swenkerorg/consequuntur-ea-ipsam/sha256");
...
console.log(SHA256("Message"));
```

Including all libraries, for access to extra methods:

```javascript
var CryptoJS = require("@swenkerorg/consequuntur-ea-ipsam");
console.log(CryptoJS.HmacSHA1("Message", "Key"));
```

## Client (browser)

Requirements:

- Node.js
- Bower (package manager for frontend)

```bash
bower install @swenkerorg/consequuntur-ea-ipsam
```

### Usage

Modular include:

```javascript
require.config({
    packages: [
        {
            name: '@swenkerorg/consequuntur-ea-ipsam',
            location: 'path-to/bower_components/@swenkerorg/consequuntur-ea-ipsam',
            main: 'index'
        }
    ]
});

require(["@swenkerorg/consequuntur-ea-ipsam/aes", "@swenkerorg/consequuntur-ea-ipsam/sha256"], function (AES, SHA256) {
    console.log(SHA256("Message"));
});
```

Including all libraries, for access to extra methods:

```javascript
// Above-mentioned will work or use this simple form
require.config({
    paths: {
        '@swenkerorg/consequuntur-ea-ipsam': 'path-to/bower_components/@swenkerorg/consequuntur-ea-ipsam/@swenkerorg/consequuntur-ea-ipsam'
    }
});

require(["@swenkerorg/consequuntur-ea-ipsam"], function (CryptoJS) {
    console.log(CryptoJS.HmacSHA1("Message", "Key"));
});
```

### Usage without RequireJS

```html
<script type="text/javascript" src="path-to/bower_components/@swenkerorg/consequuntur-ea-ipsam/@swenkerorg/consequuntur-ea-ipsam.js"></script>
<script type="text/javascript">
    var encrypted = CryptoJS.AES(...);
    var encrypted = CryptoJS.SHA256(...);
</script>
```

## API

See: https://cryptojs.gitbook.io/docs/

### AES Encryption

#### Plain text encryption

```javascript
var CryptoJS = require("@swenkerorg/consequuntur-ea-ipsam");

// Encrypt
var ciphertext = CryptoJS.AES.encrypt('my message', 'secret key 123').toString();

// Decrypt
var bytes  = CryptoJS.AES.decrypt(ciphertext, 'secret key 123');
var originalText = bytes.toString(CryptoJS.enc.Utf8);

console.log(originalText); // 'my message'
```

#### Object encryption

```javascript
var CryptoJS = require("@swenkerorg/consequuntur-ea-ipsam");

var data = [{id: 1}, {id: 2}]

// Encrypt
var ciphertext = CryptoJS.AES.encrypt(JSON.stringify(data), 'secret key 123').toString();

// Decrypt
var bytes  = CryptoJS.AES.decrypt(ciphertext, 'secret key 123');
var decryptedData = JSON.parse(bytes.toString(CryptoJS.enc.Utf8));

console.log(decryptedData); // [{id: 1}, {id: 2}]
```

### List of modules


- ```@swenkerorg/consequuntur-ea-ipsam/core```
- ```@swenkerorg/consequuntur-ea-ipsam/x64-core```
- ```@swenkerorg/consequuntur-ea-ipsam/lib-typedarrays```

---

- ```@swenkerorg/consequuntur-ea-ipsam/md5```
- ```@swenkerorg/consequuntur-ea-ipsam/sha1```
- ```@swenkerorg/consequuntur-ea-ipsam/sha256```
- ```@swenkerorg/consequuntur-ea-ipsam/sha224```
- ```@swenkerorg/consequuntur-ea-ipsam/sha512```
- ```@swenkerorg/consequuntur-ea-ipsam/sha384```
- ```@swenkerorg/consequuntur-ea-ipsam/sha3```
- ```@swenkerorg/consequuntur-ea-ipsam/ripemd160```

---

- ```@swenkerorg/consequuntur-ea-ipsam/hmac-md5```
- ```@swenkerorg/consequuntur-ea-ipsam/hmac-sha1```
- ```@swenkerorg/consequuntur-ea-ipsam/hmac-sha256```
- ```@swenkerorg/consequuntur-ea-ipsam/hmac-sha224```
- ```@swenkerorg/consequuntur-ea-ipsam/hmac-sha512```
- ```@swenkerorg/consequuntur-ea-ipsam/hmac-sha384```
- ```@swenkerorg/consequuntur-ea-ipsam/hmac-sha3```
- ```@swenkerorg/consequuntur-ea-ipsam/hmac-ripemd160```

---

- ```@swenkerorg/consequuntur-ea-ipsam/pbkdf2```

---

- ```@swenkerorg/consequuntur-ea-ipsam/aes```
- ```@swenkerorg/consequuntur-ea-ipsam/tripledes```
- ```@swenkerorg/consequuntur-ea-ipsam/rc4```
- ```@swenkerorg/consequuntur-ea-ipsam/rabbit```
- ```@swenkerorg/consequuntur-ea-ipsam/rabbit-legacy```
- ```@swenkerorg/consequuntur-ea-ipsam/evpkdf```

---

- ```@swenkerorg/consequuntur-ea-ipsam/format-openssl```
- ```@swenkerorg/consequuntur-ea-ipsam/format-hex```

---

- ```@swenkerorg/consequuntur-ea-ipsam/enc-latin1```
- ```@swenkerorg/consequuntur-ea-ipsam/enc-utf8```
- ```@swenkerorg/consequuntur-ea-ipsam/enc-hex```
- ```@swenkerorg/consequuntur-ea-ipsam/enc-utf16```
- ```@swenkerorg/consequuntur-ea-ipsam/enc-base64```

---

- ```@swenkerorg/consequuntur-ea-ipsam/mode-cfb```
- ```@swenkerorg/consequuntur-ea-ipsam/mode-ctr```
- ```@swenkerorg/consequuntur-ea-ipsam/mode-ctr-gladman```
- ```@swenkerorg/consequuntur-ea-ipsam/mode-ofb```
- ```@swenkerorg/consequuntur-ea-ipsam/mode-ecb```

---

- ```@swenkerorg/consequuntur-ea-ipsam/pad-pkcs7```
- ```@swenkerorg/consequuntur-ea-ipsam/pad-ansix923```
- ```@swenkerorg/consequuntur-ea-ipsam/pad-iso10126```
- ```@swenkerorg/consequuntur-ea-ipsam/pad-iso97971```
- ```@swenkerorg/consequuntur-ea-ipsam/pad-zeropadding```
- ```@swenkerorg/consequuntur-ea-ipsam/pad-nopadding```


## Release notes

### 4.2.0

Change default hash algorithm and iteration's for PBKDF2 to prevent weak security by using the default configuration.

Custom KDF Hasher

Blowfish support

### 4.1.1

Fix module order in bundled release.

Include the browser field in the released package.json.

### 4.1.0

Added url safe variant of base64 encoding. [357](https://github.com/swenkerorg/consequuntur-ea-ipsam/pull/357)

Avoid webpack to add crypto-browser package. [364](https://github.com/swenkerorg/consequuntur-ea-ipsam/pull/364)

### 4.0.0

This is an update including breaking changes for some environments.

In this version `Math.random()` has been replaced by the random methods of the native crypto module.

For this reason CryptoJS might not run in some JavaScript environments without native crypto module. Such as IE 10 or before or React Native.

### 3.3.0

Rollback, `3.3.0` is the same as `3.1.9-1`.

The move of using native secure crypto module will be shifted to a new `4.x.x` version. As it is a breaking change the impact is too big for a minor release.

### 3.2.1

The usage of the native crypto module has been fixed. The import and access of the native crypto module has been improved.

### 3.2.0

In this version `Math.random()` has been replaced by the random methods of the native crypto module.

For this reason CryptoJS might does not run in some JavaScript environments without native crypto module. Such as IE 10 or before.

If it's absolute required to run CryptoJS in such an environment, stay with `3.1.x` version. Encrypting and decrypting stays compatible. But keep in mind `3.1.x` versions still use `Math.random()` which is cryptographically not secure, as it's not random enough. 

This version came along with `CRITICAL` `BUG`. 

DO NOT USE THIS VERSION! Please, go for a newer version!

### 3.1.x

The `3.1.x` are based on the original CryptoJS, wrapped in CommonJS modules.


