# JavaScript Drum Kit 学习笔记

## 实现效果

用户按下我们指定的按键ASDFGHJKL ，播放对应按键的音乐。

[演示效果](http://codepen.io/iamscottcox/full/gLjYjB/)

## 一些基础语法和关键点

1、键盘事件

添加键盘事件监听，获取对应按键的的ASCII编码值并且赋予给定义好的**keycode**属性。具体的按键的ASCII编码，可以在[这个网站](http://keycode.info/)查看。

如下代码所示：

```
const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
const key = document.querySelector(`div[data-key="${e.keyCode}"]`);
```

2、改变样式

当用户按下指定的按键时，在对应的元素上添加**playing**类来控制动画效果。

由于动画效果是使用**transition**来实现的，所以，只要监听按钮的**transitionend**事件来控制动画效果。


```
function removeTransition(e) {
      if (e.propertyName !== 'transform') return; // 如果没有transform事件 那就跳过此方法
      this.classList.remove('playing');
    }

    const keys = document.querySelectorAll('.key'); // 找到所有带 key 这个类的元素并赋予给变量 keys
    keys.forEach(key => key.addEventListener('transitionend', removeTransition));
```

## ES6语法

1、const：声明一个只读的常量，标识符的值只能赋值一次。

2、模板字面量（Template literals）中用于表示模板字符串的标识。特点是字符串首尾用反引号（`），内部的模板部分用 ${ } 括起来表示，具体请看MDN文档。


```
const soundclip = document.querySelector(`audio[data-key="${e.keyCode}"]`);
      const keyelement = document.querySelector(`.key[data-key="${e.keyCode}"]`);
```

详细可以查看源代码。







