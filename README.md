# JSON edits JSON
Spec

```JSON
// Source JSON
{
  "hoge": {
    "fuga": 10,
    "list": ["item1", "item2"]
  },
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
  "foo": 30,
  "arr": [100,2,3],
  "newKey": {"anykey": "anyvalue"},
  "obj": {"all": "replaced"}
}
```

## 考えられる用途
* 多言語対応のとき、オリジナルファイルへのテキストデータの注入
* 既存のJSONデータへの差分データの汎用的な適用。データのアップデート
* それを利用したゲームデータのModding

