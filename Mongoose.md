# Mongoose对象API 

[TOC] 



### [Mongoose()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose)

Mongoose的构造函数。

mongoose模块的exports对象是该类的一个实例。大多数应用程序将只使用这一个实例。

```js
const mongoose = require('mongoose');
mongoose instanceof mongoose.Mongoose; // true

// Create a new Mongoose instance with its own `connect()`, `set()`, `model()`, etc.
const m = new mongoose.Mongoose();
```

### [Mongoose.prototype.Aggregate()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Aggregate)

Mongoose聚合构造函数

### [Mongoose.prototype.CastError()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-CastError)

Mongoose CastError构造函数。

### [Mongoose.prototype.Collection()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Collection)

Mongoose集合构造函数

### [Mongoose.prototype.Connection()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Connection)

Mongoose连接构造函数

### [Mongoose.prototype.Date](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Date)

Mongoose 的Date类型。

```js
const schema = new Schema({ test: Date });
schema.path('test') instanceof mongoose.Date; // true
```

### [Mongoose.prototype.Document()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Document)

Mongoose文档构造器。

### [Mongoose.prototype.DocumentProvider()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-DocumentProvider)

Mongoose文档提供程序构造函数。Mongoose用户不应该直接使用这个。

### [Mongoose.prototype.Error()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Error)

MongooseError构造函数

### [Mongoose.prototype.Mixed](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Mixed)

Mongoose 的Mixed 类型。用于声明Mongoose的更改跟踪、转换和验证应该忽略的模式中的路径。

```js
const schema = new Schema({ arbitrary: mongoose.Mixed });
```

### [Mongoose.prototype.Model()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Model)

Mongoose模型构造器。

### [Mongoose.prototype.Mongoose()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Mongoose)

Mongoose 构造函数。

mongoose模块的导出就是此类的一个实例。

```js
const mongoose = require('mongoose');
const mongoose2 = new mongoose.Mongoose();
```

### [Mongoose.prototype.Number](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Number)

Mongoose 的Number 类型。用于声明模式中Mongoose应该转换为数字的path。

```js
const schema = new Schema({ num: mongoose.Number });
// Equivalent to:
const schema = new Schema({ num: 'number' });
```

### [Mongoose.prototype.ObjectId](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-ObjectId)

Mongoose的ObjectId 类型。用于声明模式中的路径，这些路径应该是MongoDB对象。不要使用它来创建新的ObjectId实例，请使用mongoo . types。ObjectId代替。

```js
const childSchema = new Schema({ parentId: mongoose.ObjectId });
```

### [Mongoose.prototype.Promise](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Promise)

Mongoose Promise构造器。

### [Mongoose.prototype.PromiseProvider()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-PromiseProvider)

存储层的mongoose 承诺

### [Mongoose.prototype.Query()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Query)

Mongoose查询[Query](https://mongoosejs.com/docs/api/mongoose.html#query_Query) 构造函数。

### [Mongoose.prototype.STATES](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-STATES)

为用户地公开连接状态

### [Mongoose.prototype.Schema()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-Schema)

Mongoose模式[Schema](https://mongoosejs.com/docs/api/mongoose.html#schema_Schema)的构造器。

```js
const mongoose = require('mongoose');
const Schema = mongoose.Schema;
const CatSchema = new Schema(..);
```

### [Mongoose.prototype.connect()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-connect)

```js
mongoose.connect('mongodb://user:pass@localhost:port/database');

// replica sets
const uri = 'mongodb://user:pass@localhost:port,anotherhost:port,yetanother:port/mydatabase';
mongoose.connect(uri);

// with options
mongoose.connect(uri, options);

// optional callback that gets fired when initial connection completed
const uri = 'mongodb://nonexistent.domain:27000';
mongoose.connect(uri, function(error) {
  // if error is truthy, the initial connection failed.
})
```

### [Mongoose.prototype.connection](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-connection)

Mongoose模块的默认连接。相当于mongoose.connections[0]，查看[`connections`](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-connections)。

```js
const mongoose = require('mongoose');
mongoose.connect(...);
mongoose.connection.on('error', cb);
```

这是使用mongoo .model创建的每个模型默认使用的连接。

创建一个新连接，使用 [`createConnection()`](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-createConnection)

### [Mongoose.prototype.connections](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-connections)

一个数组，包含与这个Mongoose实例关联的所有连接。默认情况下，有一个连接。调用createConnection()将向这个数组添加一个连接。

```js
const mongoose = require('mongoose');
mongoose.connections.length; // 1, just the default connection
mongoose.connections[0] === mongoose.connection; // true

mongoose.createConnection('mongodb://localhost:27017/test');
mongoose.connections.length; // 2
```

### [Mongoose.prototype.createConnection()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-createConnection)

创建一个连接实例。

每个连接实例映射到一个单独的数据库。这个方法在管理多个db连接时很有帮助。

传递的选项优先于连接字符串中包含的选项

```js
// with mongodb:// URI
db = mongoose.createConnection('mongodb://user:pass@localhost:port/database');

// and options
const opts = { db: { native_parser: true }}
db = mongoose.createConnection('mongodb://user:pass@localhost:port/database', opts);

// replica sets
db = mongoose.createConnection('mongodb://user:pass@localhost:port,anotherhost:port,yetanother:port/database');

// and options
const opts = { replset: { strategy: 'ping', rs_name: 'testSet' }}
db = mongoose.createConnection('mongodb://user:pass@localhost:port,anotherhost:port,yetanother:port/database', opts);

// and options
const opts = { server: { auto_reconnect: false }, user: 'username', pass: 'mypassword' }
db = mongoose.createConnection('localhost', 'database', port, opts)

// initialize now, connect later
db = mongoose.createConnection();
db.openUri('localhost', 'database', port, [opts]);
```

### [Mongoose.prototype.deleteModel()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-deleteModel)

从默认连接中删除模型名称(如果存在的话)。您可以使用这个函数来清除您在测试中创建的任何模型，以防止OverwriteModelErrors

等价于mongoose.connection.deleteModel(name)

```js
mongoose.model('User', new Schema({ name: String }));
console.log(mongoose.model('User')); // Model object
mongoose.deleteModel('User');
console.log(mongoose.model('User')); // undefined

// Usually useful in a Mocha `afterEach()` hook
afterEach(function() {
  mongoose.deleteModel(/.+/); // Delete every model
});
```

### [Mongoose.prototype.disconnect()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-disconnect)

断开连接

在 所有并行连接上，执行.close()。

### [Mongoose.prototype.get()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-get)

获取mongoose的options

```js
mongoose.get('test') // returns the 'test' value
```

### [Mongoose.prototype.isValidObjectId()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-isValidObjectId)

如果Mongoose可以将给定值强制转换为ObjectId，则返回true;否则返回false。

```js
mongoose.isValidObjectId(new mongoose.Types.ObjectId()); // true
mongoose.isValidObjectId('0123456789ab'); // true
mongoose.isValidObjectId(6); // false
```

### [Mongoose.prototype.model()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-model)

定义一个模型或检索一个模型。

在mongoose实例上定义的模型对同一mongoose实例创建的所有连接可用。

如果您调用mongoose.model()，使用两倍相同的名称但使用不同的模式，您将得到一个OverwriteModelError。如果您使用相同的名称和相同的模式调用mongoo .model()，您将得到相同的模式。

```js
const mongoose = require('mongoose');

// define an Actor model with this mongoose instance
const schema = new Schema({ name: String });
mongoose.model('Actor', schema);

// create a new connection
const conn = mongoose.createConnection(..);

// create Actor model
const Actor = conn.model('Actor', schema);
conn.model('Actor') === Actor; // true
conn.model('Actor', schema) === Actor; // true, same schema
conn.model('Actor', schema, 'actors') === Actor; // true, same schema and collection name

// This throws an `OverwriteModelError` because the schema is different.
conn.model('Actor', new Schema({ name: String }));
```

当没有传递集合参数时，Mongoose使用模型名。如果您不喜欢这种行为，可以传递集合名称、使用mongoo .pluralize()或设置您的模式集合名称选项。

```js
const schema = new Schema({ name: String }, { collection: 'actor' });

// or

schema.set('collection', 'actor');

// or

const collectionName = 'actor'
const M = mongoose.model('Actor', schema, collectionName)
```

### [Mongoose.prototype.now()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-now)

当设置时间戳时，Mongoose使用此函数获得当前时间。您可以使用像Sinon这样的工具进行测试来终止此函数。

### [Mongoose.prototype.set()](https://mongoosejs.com/docs/api/mongoose.html#mongoose_Mongoose-set)

设置mongoose options

```js
mongoose.set('test', value) // sets the 'test' option to `value`

mongoose.set('debug', true) // enable logging collection methods + arguments to the console/file

mongoose.set('debug', function(collectionName, methodName, ...methodArgs) {}); // use custom function to log collection methods + arguments
```