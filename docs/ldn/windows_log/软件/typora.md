<!-- 说明 -->

- **Windows 234**

## Typora安装与激活

------

!> 如果后面使用有问题就按照下面的方式试一下，现在使用暂时没有问题的情况下尽量不动它。

### 1. 官网下载

[Typora 官方中文站](https://typoraio.cn/)

### 2. 激活脚本

[Typora激活脚本_脚本之家typora-CSDN博客](https://blog.csdn.net/qq_32394351/article/details/142143469)

学习大佬解决问题的方式和编码思路

```python
# typora软件激活脚本
# https://blog.csdn.net/weixin_73609038/article/details/137751767
# https://blog.csdn.net/weixin_73609038/article/details/134021764
# https://typoraio.cn/
import os
import ctypes
import sys
 
 
def is_admin():
    try:
        return ctypes.windll.shell32.IsUserAnAdmin()
    except:
        return False
 
 
def apply_admin():
    if not is_admin():
        ctypes.windll.shell32.ShellExecuteW(None, "runas", sys.executable, __file__, None, 1)
 
 
def modify_file(_path, _old, _new):
    if not os.path.exists(_path):
        return False
 
    with open(_path, encoding='utf-8') as f:
        license_content = f.read()
 
    print(f'{_path} file_size:{len(license_content)}')
    if _old in license_content:
        license_content = license_content.replace(_old, _new)
        with open(_path, mode='w+', encoding='utf-8') as f:
            f.write(license_content)
        return True
    return False
 
 
def active_soft(bin_path=r'C:\Program Files\Typora'):
    js_path = os.path.join(bin_path, r'resources\page-dist\static\js')
    js_files = os.listdir(js_path)
    # ===== 修改 LicenseIndex*.js文件
    license_js = os.path.join(js_path, [js_file for js_file in js_files if 'LicenseIndex' in js_file][0])
    modify_file(license_js, 'e.hasActivated="true"==e.hasActivated', 'e.hasActivated="true"=="true"')
    # ===== 修改 license.html 文件
    license_html = os.path.join(bin_path, r'resources\page-dist\license.html')
    modify_file(license_html, '</body></html>',
                '</body><script>window.onload=function(){setTimeout(()=>{window.close();},5);}</script></html>')
    # ===== 修改 Panel.json  文件
    panel_json = os.path.join(bin_path, r'resources\locales\zh-Hans.lproj\Panel.json')
    modify_file(panel_json, '"UNREGISTERED":"未激活"',
                '"UNREGISTERED":" "')
    print('============激活完毕,请自行检查软件是否正常===============')
    print('请手动给快捷方式添加目标 -disable-gpu-sandbox')
 
 
def main():
    apply_admin()
    soft_path = input('请输入typora软件的安装路径,默认值为(C:\Program Files\Typora):\n')
    if soft_path:
        active_soft(soft_path)
    else:
        active_soft()
 
 
if __name__ == '__main__':
    main()
```

