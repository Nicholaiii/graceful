# [**@ocalan/graceful**](https://github.com/ocalan/graceful)

> Gracefully exit server (Koa), database (Mongo/Mongoose), Redis clients, Bree job schedulers, Bull job schedulers, and custom handlers.

> Forked from [@ladjs/graceful](https://github.com/ladjs/graceful) to add TypeScript definitions.


## Table of Contents

* [Install](#install)
* [Usage](#usage)
* [Contributors](#contributors)
* [License](#license)


## Install

[npm][]:

```sh
npm install @ocalan/graceful
```

[yarn][]:

```sh
yarn add @ocalan/graceful
```


## Usage

Using this package will bind process event listeners when `graceful.listen()` is called:

* `process.on('warning')` - will output via `config.logger.warn`
* `process.on('unhandledRejection')` - will output via `config.logger.error`
* `process.once('uncaughtException')` - will output via `config.logger.error` and `process.exit(1)` (*does not exit gracefully*)
* `process.on('message')` - support Windows (e.g. signals not available) and listen for message of `shutdown` and then exit gracefully
* `process.once('SIGTERM')` - will exit gracefully
* `process.once('SIGHUP')` - will exit gracefully
* `process.once('SIGINT')` - will exit gracefully
* `process.once('SIGUSR2')` - will exit gracefully (nodemon support)

This package also prevents multiple process/SIG events from triggering multiple graceful exits. Only one graceful exit can occur at a time.

See one of these following files from [Lad][] for the most up to date usage example:

* API - <https://github.com/ladjs/lad/blob/master/template/api.js>
* Web - <https://github.com/ladjs/lad/blob/master/template/web.js>
* Bull - <https://github.com/ladjs/lad/blob/master/template/bull.js>
* Proxy - <https://github.com/ladjs/lad/blob/master/template/proxy.js>

You can also read more about Bree at <https://github.com/breejs/bree>.


## Contributors

| Name                | Website                        |
| ------------------- | ------------------------------ |
| **Nick Baugh**      | <http://niftylettuce.com/>     |
| **Felix Mosheev**   | <https://github.com/felixmosh> |
| **Nicholai Nissen** | <https://nicholai.dev>         |


## License

[MIT](LICENSE) © [Nicholai Nissen](https://nicholai.dev)


##

[npm]: https://www.npmjs.com/

[yarn]: https://yarnpkg.com/

[lad]: https://lad.js.org
