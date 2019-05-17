Promise-mysql
==================
[![Build Status](https://travis-ci.org/lukeb-uk/node-promise-mysql.svg?style=flat&branch=master)](https://travis-ci.org/lukeb-uk/node-promise-mysql?branch=master)
[![Greenkeeper badge](https://badges.greenkeeper.io/lukeb-uk/node-promise-mysql.svg)](https://greenkeeper.io/)

Promise-mysql is a wrapper for [mysqljs/mysql](https://github.com/mysqljs/mysql) that wraps function calls with [Bluebird](https://github.com/petkaantonov/bluebird/) promises.

## API

### mysql.createConnection(connectionOptions)
This will return a the promise of a [connection](#connection) object.

#### Parameters
`connectionOptions` _object_: A [connectionOptions](#connectionOptions) object

#### Return value
A Bluebird `Promise` that resolves to a [connection](#connection) object

### mysql.createPool(connectionOptions)
This will return a the promise of a [pool](#pool) object.

#### Parameters
`connectionOptions` _object_: A [connectionOptions](#connectionOptions) object

#### Return value
A Bluebird `Promise` that resolves to a [pool](#pool) object

### connectionOptions object

In addition to the [connection options in mysqljs/mysql](https://github.com/mysqljs/mysql#connection-options), promise-mysql accepts the following:

`returnArgumentsArray` _boolean_: If set to true then methods will return an array with the return value and the callback arguments from the underlying method.

`mysqlWrapper` _function_: A function that is passed the `mysql` object so that it can be wrapped with something like the [aws-xray-sdk module](https://www.npmjs.com/package/aws-xray-sdk). This function must either return the wrapped `mysql` object, return a promise of the wrapped `mysql` object or call the callback that is passed into the function.

#### Function arguments

`mysql` _mysql object_: The mysql object

`callback(error, success)` _function_: A node-style callback that can be used to pass the wrapped version of the mysql object out of the wrapper function.

### Connection object methods

`connection.query`: Perform a query. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#performing-queries)

`connection.queryStream`: Perform a query, but return the query object for streaming. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#streaming-query-rows)

`connection.beginTransaction`: Begin a transaction. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#transactions)

`connection.commit`: Commit a transaction. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#transactions)

`connection.rollback`: Roll back a transaction. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#transactions)

`connection.changeUser`: Change the current connected user. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#switching-users-and-altering-connection-state)

`connection.ping`: Send a ping to the server. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#ping)

`connection.end`: End the connection. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#terminating-connections)

`connection.destroy`: Destroy the connection. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#terminating-connections)

`connection.pause`: Pause a connection. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#streaming-query-rows)

`connection.resume`: Resume a connection. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#streaming-query-rows)

`connection.escape`: Escape query values. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#escaping-query-values)

`connection.escapeId`: Escape query identifiers. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#escaping-query-identifiers)

`connection.format`: Prepare a query. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql#preparing-queriess)

`connection.on`: Add a listener to the connection object. See [mysqljs/mysql documentation](https://github.com/mysqljs/mysql) for events that may be listened for.
