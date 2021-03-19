# Schema对象API

### [Schema()](https://mongoosejs.com/docs/api/schema.html#schema_Schema)

Schema constructor.

```js
const child = new Schema({ name: String });
const schema = new Schema({ name: String, age: Number, children: [child] });
const Tree = mongoose.model('Tree', schema);

// setting schema options
new Schema({ name: String }, { _id: false, autoIndex: false })
```

配置选项：

详情需要时间看的 ：https://mongoosejs.com/docs/guide.html

