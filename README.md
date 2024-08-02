# UseTritonInPaddle




- 由于triton源码中部分util函数（如检查当前机器的计算能力，检查当前机器的idx）依赖了triton，这对于paddle用户想要使用triton不是很友好。
- 故此项目，将triton源码中的部分依赖triton的代码，替换为paddle的代码。
- 使用方式，用户只需要安装`python3.8 -m pip install use_triton_in_paddle`即可。


```py
import use_triton_in_paddle
use_triton_in_paddle.make_triton_compatible_with_paddle()
```
- 会自动将triton内部的`import torch`换成`import use_triton_in_paddle as torch`
- 当然看起来换成

```py
try:
    import torch
except:
    print("No module named 'torch', we will use_triton_in_paddle as torch inside triton")
    import use_triton_in_paddle as torch
```

- 然后就可以在paddle中正常使用triton了。和torch的用法一摸一样















