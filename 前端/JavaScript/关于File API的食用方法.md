# Files 的食用方法

## File API

File API 为 JS 自带的 API

示例：

```JavaScript
let
    fileInput = document.getElementById('test-image-file'), //这个是一个type=files的input
    preview = document.getElementById('test-image-preview');

// 监听change事件:
fileInput.addEventListener('change', function () {
    // 读取文件:
    let file = fileInput.files[0];
    let reader = new FileReader();
    reader.onload = function(e) {
        let data = e.target.result; // 'data:image/jpeg;base64,/9j/4AAQSk...(base64编码)...'
        preview.style.backgroundImage = 'url(' + data + ')';
    };
    // 以DataURL的形式读取文件:
    reader.readAsDataURL(file);
});
```

**解释**：

选择文件后，文件都会以 `filelist` 对象返回一个所有文件列表，并且以 `files` 属性保存。可以通过访问该属性获取用户上传的文件。

需要定义一个 `FileReader` 对象，并起名 reader。该对象可以用来打开文件。

使用 `readAsDataURL()` 来读取文件的具体内容。

之后进入 reader 的 `onload` 回调函数，该函数会将文件作为参数放入回调函数，`e.target.result` 可以获得文件的一个本地链接

这里 `onload` 为异步调用，如果 `reader.readAsDataURL(file)`后面还有代码则会继续执行，同时同步执行 `onload` 当中的代码。

## 使用 URL.createObjectURL() 创建本地图片的链接

在上面当中直接把 `e.target.result` 作为图片的url，很长而会显得臃肿。

如果只是在前端使用，可以用`URL.createObjectURL()`

```Javascript
    let
        fileInput = document.getElementById('test-image-file'),
        preview = document.getElementById('test-image-preview');

    // 监听change事件:
    fileInput.addEventListener('change', function () {
        let url = window.URL.createObjectURL(fileInput.files[0]);
        preview.style.backgroundImage = 'url('+url+')';
    });
```

**原型：**`objectURL = URL.createObjectURL(object);`

`object` 参数接受 `File`、`blob`、`MediaSource` 对象

因此可以直接把文件传入函数调用即可
