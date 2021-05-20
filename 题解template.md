# 回溯
```python
def backtrack("原始参数") {
    //终止条件(递归必须要有终止条件)
    if ("终止条件"):
        //一些逻辑操作（可有可无，视情况而定）
        return

    for i in range("for循环开始的参数", "for循环结束的参数"):
        //一些逻辑操作（可有可无，视情况而定）

        //做出选择

        //递归
        backtrack("新的参数")
        //一些逻辑操作（可有可无，视情况而定）

        //撤销选择
   return
```
# 背包问题

# dictionary以value sort
sorted_dict = sorted(dict_exmaple.items(), key=lambda x: x[1], reverse=True)
