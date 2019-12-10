# JSON edits JSON
## Simple version spec

```JSON
// Source JSON
{
  "hoge": {
    "fuga": 10,
    "list": ["item1", "item2"]
  },
  "str": "any text",
  "foo": 30,
  "arr": [1,2,3],
  "obj": {"a": 1, "b": 2, "c": 3}
}
```
# *
```JSON
// JEJ JSON
{
  "hoge.fuga": 20,
  "hoge.list[0]": "moddedItem1",
  "hoge.list[2]": "addedItem3",
  "arr[0]": 100,
  "newKey": {"anykey": "anyvalue"},
  "obj": {"all": "replaced"}
}
```
# =
```JSON
// Result JSON
{
  "hoge": {
    "fuga": 20,
    "list": ["moddedItem1", "item2", "addedItem2"]
  },
  "str": "any text",
  "foo": 30,
  "arr": [100,2,3],
  "newKey": {"anykey": "anyvalue"},
  "obj": {"all": "replaced"}
}
```

## Complex version spec
```JSON
// Same JEJ as before with complex version
[
  ["set", "hoge.fuga", 20],
  ["set", "hoge.list[0]", "moddedItem1"],
  ["append", "hoge.list", "moddedItem3"],
  ["set", "arr[0]", 100],
  ["set", "newKey", {"anykey": "anyvalue"}],
  ["set", "obj", {"all": "replaced"}]
]
```
### 2
```JSON
// Complex version only functions
[
  ["insert", "hoge.list[1]", 10],
  ["remove", "hoge.list[1]"],
  ["remove", "newKey.anykey"],
  ["appendString", "str", "!!"],
  ["add", "foo", 0.5],
  ["multiply", "foo", 0.5],
  ["divide", "foo", 0.5],
  ["modulo", "foo", 2],
]
```
* Object -> Simple version
* Array -> Complex version


## 考えられる用途
* 多言語対応のとき、オリジナルファイルへのテキストデータの注入
* 既存のJSONデータへの差分データの汎用的な適用。データのアップデート
* それを利用したゲームデータのModding

