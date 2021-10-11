# 5. 在虚拟环境中使用 Jupyter Notebok

## 1. 查看

```python
import os
import sys

print(sys.executable)  # path of python.exe
print(sys.version)
print(sys.version_info)
```

\>\>\>

```
D:\anaconda3\python.exe
3.8.3 (default, Jul  2 2020, 17:30:36) [MSC v.1916 64 bit (AMD64)]
sys.version_info(major=3, minor=8, micro=3, releaselevel='final', serial=0)
```

## 2. 安装包 ipykernel, nb_conda

1. 激活目标虚拟环境
2. `pip install ipykernel`
    - 只装了 ipykernel 不生效
    - 页面的 new 中只多了个 Spider
3. `conda install nb_conda`
    - 这里需要用 conda，会提醒安装一些依赖，输入 y 即可
    - 激活前，即默认环境安装 `nb_conda_kernels` 不生效
    - 页面的 new 中多了
        - Python [conda env: Spider] *
        - Python [conda env: root]

## 3. 使用

- 命令格式：`python -m ipykernel install --name {your_env_name}`

```
(Spider) D:\>python -m ipykernel install --name Spider
Installed kernelspec Spider in C:\ProgramData\jupyter\kernels\spider
```

## 4. 再次打开 Jupyter Notebook

```
D:\>conda activate Spider

(Spider) D:\>jupyter notebook
```

- ps
    - 刷新老的页面不管用，需要在新起的页面中工作
    - 以前的笔记用的仍然是 base env
    - 想用虚拟环境，需要点击右上角的 <kbd>new</kbd> > <kbd>Spider</kbd>
    - 笔记页面中可以选择 Kernel > Change kernel > 相应环境

## 5. 一些命令

```
D:\>jupyter kernelspec list
Available kernels:
  python3    D:\anaconda3\share\jupyter\kernels\python3
  spider     C:\ProgramData\jupyter\kernels\spider

D:\>conda info -e
# conda environments:
#
base                  *  D:\anaconda3
Spider                   D:\anaconda3\envs\Spider
django_35                D:\anaconda3\envs\django_35
django_env               D:\anaconda3\envs\django_env
```
