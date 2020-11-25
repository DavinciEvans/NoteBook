# Hello PHP!

## 字符串运算

并置：使用 ` . `

`echo $txt1 . " " . $txt2;`

`strlen()`：计算长度

`strpos()`：查找字符或者文本

`echo strpos("Hello World!", "W")`

- 返回 6

`substr($string, $start, $end)`：分割字符串

## 流程

if、 for、Switch 和 C 语言当中的一样

## 数组

`$arr = array('WOW', 'AWESOME')`

`arr[0] = 'WOW'`

求解数组长度：count()

**关联数组**：类似 python 的字典

```PHP
$age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43");
$age['Peter']="35";
$age['Ben']="37";
$age['Joe']="43";
```

使用 `foreach` 遍历

```PHP
foreach($age as $x=>$x_value)
{
    echo "Key=" . $x . ", Value=" . $x_value;
    echo "<br>";
}
```

排序：

- `sort()` - 对数组进行升序排列

- `rsort()` - 对数组进行降序排列

- `asort()` - 根据关联数组的值，对数组进行升序排列

- `ksort()` - 根据关联数组的键，对数组进行升序排列

- `arsort()` - 根据关联数组的值，对数组进行降序排列

- `krsort()` - 根据关联数组的键，对数组进行降序排列

## 超级全局变量

### $GLOBALS

一个包含了全部变量的全局组合数组。变量的名字就是数组的键

```PHP
<?php 
$x = 75; 
$y = 25;
 
function addition() 
{ 
    $GLOBALS['z'] = $GLOBALS['x'] + $GLOBALS['y']; 
}
 
addition(); 
echo $z; 
?>
```

### $_SERVER

一个包含了诸如头信息(header)、路径(path)、以及脚本位置(script locations)等等信息的数组

```PHP
<?php 
echo $_SERVER['PHP_SELF'];
echo "<br>";
echo $_SERVER['SERVER_NAME'];
echo "<br>";
echo $_SERVER['HTTP_HOST'];
echo "<br>";
echo $_SERVER['HTTP_REFERER'];
echo "<br>";
echo $_SERVER['HTTP_USER_AGENT'];
echo "<br>";
echo $_SERVER['SCRIPT_NAME'];
?>
```

### $_REQUEST

收集HTML表单提交的数据

```PHP
<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
Name: <input type="text" name="fname">
<input type="submit">
</form>
 
<?php 
$name = $_REQUEST['fname']; 
echo $name; 
?>
```

### $_POST

数组，里面为请求参数

```PHP
<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
Name: <input type="text" name="fname">
<input type="submit">
</form>
 
<?php 
$name = $_POST['fname']; 
echo $name; 
?>
```

### $_GET

一个数组，里面为请求的参数

```PHP
<html>
<body>
 
<?php 
echo "Study " . $_GET['subject'] . " @ " . $_GET['web'];
?>
 
</body>
</html>
```

- $_FILES

- $_ENV

- $_COOKIE

- $_SESSION