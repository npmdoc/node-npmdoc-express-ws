# api documentation for  [express-ws (v3.0.0)](https://github.com/HenningM/express-ws)  [![npm package](https://img.shields.io/npm/v/npmdoc-express-ws.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-express-ws) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-express-ws.svg)](https://travis-ci.org/npmdoc/node-npmdoc-express-ws)
#### WebSocket endpoints for Express applications

[![NPM](https://nodei.co/npm/express-ws.png?downloads=true)](https://www.npmjs.com/package/express-ws)

[![apidoc](https://npmdoc.github.io/node-npmdoc-express-ws/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-express-ws_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-express-ws/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-express-ws/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-express-ws/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Henning Morud",
        "email": "henning@morud.org"
    },
    "bugs": {
        "url": "https://github.com/HenningM/express-ws/issues"
    },
    "contributors": [
        {
            "name": "Jesús Leganés Combarro",
            "email": "piranna@gmail.com"
        },
        {
            "name": "Sven Slootweg",
            "email": "admin@cryto.net"
        },
        {
            "name": "Andrew Phillips",
            "email": "theasp@gmail.com"
        },
        {
            "name": "Nicholas Schell",
            "email": "nschell@gmail.com"
        },
        {
            "name": "Max Truxa",
            "email": "dev@maxtruxa.com"
        },
        {
            "name": "Kræn Hansen",
            "email": "mail@kraenhansen.dk"
        }
    ],
    "dependencies": {
        "ws": "^2.0.0"
    },
    "description": "WebSocket endpoints for Express applications",
    "devDependencies": {
        "babel-cli": "^6.5.1",
        "babel-preset-es2015": "^6.5.0",
        "eslint": "^3.15.0",
        "eslint-config-airbnb": "^14.1.0",
        "eslint-plugin-import": "^2.2.0",
        "express": "^5.0.0-alpha.1"
    },
    "directories": {
        "example": "examples"
    },
    "dist": {
        "shasum": "7ddaaf3b7c758865c099905989911b6234477dbd",
        "tarball": "https://registry.npmjs.org/express-ws/-/express-ws-3.0.0.tgz"
    },
    "engines": {
        "node": ">=4.5.0"
    },
    "gitHead": "7afeb2f04f94d6400fa1f99e1c097b796ff9d410",
    "homepage": "https://github.com/HenningM/express-ws",
    "keywords": [
        "express",
        "ws",
        "websocket"
    ],
    "license": "BSD-2-Clause",
    "main": "index.js",
    "maintainers": [
        {
            "name": "henningm",
            "email": "henning@morud.org"
        }
    ],
    "name": "express-ws",
    "optionalDependencies": {},
    "peerDependencies": {
        "express": "^4.0.0 || ^5.0.0-alpha.1"
    },
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/HenningM/express-ws.git"
    },
    "scripts": {
        "build": "babel src/ -d lib/",
        "lint": "eslint src/",
        "prepublish": "npm run build"
    },
    "version": "3.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module express-ws](#apidoc.module.express-ws)
1.  object <span class="apidocSignatureSpan">express-ws.</span>add_ws_method
1.  object <span class="apidocSignatureSpan">express-ws.</span>trailing_slash
1.  object <span class="apidocSignatureSpan">express-ws.</span>websocket_url
1.  object <span class="apidocSignatureSpan">express-ws.</span>wrap_middleware

#### [module express-ws.add_ws_method](#apidoc.module.express-ws.add_ws_method)
1.  [function <span class="apidocSignatureSpan">express-ws.add_ws_method.</span>default (target)](#apidoc.element.express-ws.add_ws_method.default)

#### [module express-ws.trailing_slash](#apidoc.module.express-ws.trailing_slash)
1.  [function <span class="apidocSignatureSpan">express-ws.trailing_slash.</span>default (string)](#apidoc.element.express-ws.trailing_slash.default)

#### [module express-ws.websocket_url](#apidoc.module.express-ws.websocket_url)
1.  [function <span class="apidocSignatureSpan">express-ws.websocket_url.</span>default (url)](#apidoc.element.express-ws.websocket_url.default)

#### [module express-ws.wrap_middleware](#apidoc.module.express-ws.wrap_middleware)
1.  [function <span class="apidocSignatureSpan">express-ws.wrap_middleware.</span>default (middleware)](#apidoc.element.express-ws.wrap_middleware.default)



# <a name="apidoc.module.express-ws"></a>[module express-ws](#apidoc.module.express-ws)



# <a name="apidoc.module.express-ws.add_ws_method"></a>[module express-ws.add_ws_method](#apidoc.module.express-ws.add_ws_method)

#### <a name="apidoc.element.express-ws.add_ws_method.default"></a>[function <span class="apidocSignatureSpan">express-ws.add_ws_method.</span>default (target)](#apidoc.element.express-ws.add_ws_method.default)
- description and source-code
```javascript
function addWsMethod(target) {
<span class="apidocCodeCommentSpan">  /* This prevents conflict with other things setting '.ws'. */
</span>  if (target.ws === null || target.ws === undefined) {
    target.ws = function addWsRoute(route) {
      for (var _len = arguments.length, middlewares = Array(_len > 1 ? _len - 1 : 0), _key = 1; _key < _len; _key++) {
        middlewares[_key - 1] = arguments[_key];
      }

      var wrappedMiddlewares = middlewares.map(_wrapMiddleware2.default);

      /* We append '/.websocket' to the route path here. Why? To prevent conflicts when
       * a non-WebSocket request is made to the same GET route - after all, we are only
       * interested in handling WebSocket requests.
       *
       * Whereas the original 'express-ws' prefixed this path segment, we suffix it -
       * this makes it possible to let requests propagate through Routers like normal,
       * which allows us to specify WebSocket routes on Routers as well \o/! */
      var wsRoute = (0, _websocketUrl2.default)(route);

      /* Here we configure our new GET route. It will never get called by a client
       * directly, it's just to let our request propagate internally, so that we can
       * leave the regular middleware execution and error handling to Express. */
      this.get.apply(this, _toConsumableArray([wsRoute].concat(wrappedMiddlewares)));

      /*
       * Return 'this' to allow for chaining:
       */
      return this;
    };
  }
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.express-ws.trailing_slash"></a>[module express-ws.trailing_slash](#apidoc.module.express-ws.trailing_slash)

#### <a name="apidoc.element.express-ws.trailing_slash.default"></a>[function <span class="apidocSignatureSpan">express-ws.trailing_slash.</span>default (string)](#apidoc.element.express-ws.trailing_slash.default)
- description and source-code
```javascript
function addTrailingSlash(string) {
  var suffixed = string;
  if (suffixed.charAt(suffixed.length - 1) !== '/') {
    suffixed = suffixed + '/';
  }
  return suffixed;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.express-ws.websocket_url"></a>[module express-ws.websocket_url](#apidoc.module.express-ws.websocket_url)

#### <a name="apidoc.element.express-ws.websocket_url.default"></a>[function <span class="apidocSignatureSpan">express-ws.websocket_url.</span>default (url)](#apidoc.element.express-ws.websocket_url.default)
- description and source-code
```javascript
function websocketUrl(url) {
  if (url.indexOf('?') !== -1) {
    var _url$split = url.split('?'),
        _url$split2 = _slicedToArray(_url$split, 2),
        baseUrl = _url$split2[0],
        query = _url$split2[1];

    return (0, _trailingSlash2.default)(baseUrl) + '.websocket?' + query;
  }
  return (0, _trailingSlash2.default)(url) + '.websocket';
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.express-ws.wrap_middleware"></a>[module express-ws.wrap_middleware](#apidoc.module.express-ws.wrap_middleware)

#### <a name="apidoc.element.express-ws.wrap_middleware.default"></a>[function <span class="apidocSignatureSpan">express-ws.wrap_middleware.</span>default (middleware)](#apidoc.element.express-ws.wrap_middleware.default)
- description and source-code
```javascript
function wrapMiddleware(middleware) {
  return function (req, res, next) {
    if (req.ws !== null && req.ws !== undefined) {
      req.wsHandled = true;
      try {
<span class="apidocCodeCommentSpan">        /* Unpack the '.ws' property and call the actual handler. */
</span>        middleware(req.ws, req, next);
      } catch (err) {
        /* If an error is thrown, let's send that on to any error handling */
        next(err);
      }
    } else {
      /* This wasn't a WebSocket request, so skip this middleware. */
      next();
    }
  };
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
