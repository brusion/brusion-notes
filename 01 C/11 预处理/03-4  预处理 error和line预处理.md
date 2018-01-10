## 一、error预处理
### #error预处理指令的作用是编译时只要遇到#error就会产生一个编译错误提示消息，并停止编译。
### 语法：#error error-message

### 注意：
* 1、error-message不用双引号
* 2、错误信息显示时可能还会显示程序预定义的其他内容

## 二、line预处理
### #line的作用是改变当前行数和文件名称，是在编译程序中预先定义的标识符。
### 语法：line number["filename"]---（文件名可以省略）

* 例如：#line 30
        
