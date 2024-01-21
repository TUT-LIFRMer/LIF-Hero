# 编译器选择问题
使用的是**arm-none-eabi-gcc.exe**编译器，注意vscode会自动根据系统的gcc编译器选择默认的gcc.exe，所以需要进入到**c_cpp_properties.json**文件中将其更换为arm-none-eabi-gcc.exe。
# 未定义标识符报错问题
在使用arm-none-eabi-gcc.exe编译器时，如果出现未定义标识符报错，可能是由于没有将**makefile**里的
```makefile
    #C defines
    C_DEFS =  \
    -DUSE_HAL_DRIVER \
    -DSTM32F407xx
```
加入到**c_cpp_properties.json**的**defines**中。
例如本工程的**c_cpp_properties.json**文件如下：
```json
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "_UNICODE",
                "USE_HAL_DRIVER",
                "STM32F407xx"
            ],
            "compilerPath": "C:\\msys64\\mingw64\\bin\\arm-none-eabi-gcc.exe",
            "cStandard": "c17",
            "cppStandard": "gnu++17",
            "intelliSenseMode": "windows-gcc-arm",
            "configurationProvider": "ms-vscode.makefile-tools"
        }
    ],
    "version": 4
}
```