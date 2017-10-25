# Node.js
回调函数     异步传输


# PHP 
## Variable 变量
###### var_dump()  //返回    数据类型  和值
```
$x = 5985;
var_dump($x);   // int(5985) 
echo PHP_EOL;     //   \n  换行符号
```


### local
### global 
    global $x,$y; 
    $GLOBALS['x'];  // 
### static  
    static x = 0;
    //每次调用该函数时，变量保留函数前一次值
parameter

## String
echo strlen("Hello World!");  // 12   字符串长度
echo strpos("Hello world!","world");
	// 6  查找字符
a.b    //连接两个字符
## 超级全局变量
### GLOBALS
```
$GLOBALS['z'];
```
### SERVER
```
echo "PHP_SELF: \n". $_SERVER['PHP_SELF'];
echo "<br>";
echo "SERVER_NAME: \n". $_SERVER['SERVER_NAME'];
echo "<br>";
echo "HTTP_HOST: \n". $_SERVER['HTTP_HOST'];
echo "<br>";
echo "HTTP_REFERER: \n". $_SERVER['HTTP_REFERER'];
echo "<br>";
echo "HTTP_USER_AGENT: \n". $_SERVER['HTTP_USER_AGENT'];
echo "<br>";
echo "SCRIPT_NAME: \n". $_SERVER['SCRIPT_NAME'];
```
### REQUEST
收集form的数据
### POST
### GET
### FILES
### ENV
### COOKIE
### SESSION

## PHP预定义常量
### LINE
```    
__LINE__
echo '这是第 " '  . __LINE__ . ' " 行';
```
### FILE
    __FILE__		
### DIR
    __DIR__
### Function
    __FUNCTION__	//函数名
### Class

    __CLASS__
    __TRAIT__
### Trait
    __TRAIT__ 
```   	
class Base {
    public function sayHello() {
        echo 'Hello ';
    }
}
trait SayWorld {
    public function sayHello() {
        parent::sayHello();
        echo 'World!';
    }
}
class MyHelloWorld extends Base {
    use SayWorld;
}
$o = new MyHelloWorld();
$o->sayHello();
```
### Method
__METHOD__
### Namespace
__NAMESPACE__

## Array数组
###### count()	//获取数组长度
```
$cars=array("AAA","BBB","CCC");
echo count($cars);    //  3
```
## 关联数组   => 
```
$age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43");
echo "Peter is " . $age['Peter'] . " years old.";
```
## forEach 遍历数组
```
$age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43"); 
foreach($age as $x=>$x_value) 
{ 
    echo "Key=" . $x . ", Value=" . $x_value; 
    echo "<br>"; 
}
```
sort() - 升序排列
rsort() - 降序排列
asort() - 根据数组的值，升序排列
ksort() - 根据数组的键，升序排列
arsort() - 根据数组的值，降序排列
krsort() - 根据数组的键，降序排列


## Email 
mail(to,subject,message,headers,parameters)
to	必需 规定 email 接收者。
subject 必需 规定 email 的主题。注释：该参数不能包含任何新行字符。
message 必需 定义要发送的消息。应使用 LF (\n) 来分隔各行。每行应该限制在 70 个字符内。
headers 可选 规定附加的标题，比如 From、Cc 和 Bcc。应当使用 CRLF (\r\n) 分隔附加的标题。
parameters	可选。对邮件发送程序规定额外的参数。


##Examples
### URl exist 
```
function urlExists($url=NULL)  {  
  if($url == NULL) return false;  
  $ch = curl_init($url);  
  curl_setopt($ch, CURLOPT_TIMEOUT, 5);  
  curl_setopt($ch, CURLOPT_CONNECTTIMEOUT, 5);  
  curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);  
  $data = curl_exec($ch);  
  $httpcode = curl_getinfo($ch, CURLINFO_HTTP_CODE);  
  curl_close($ch);  
  if($httpcode>=200 && $httpcode<300){  
      return true;  
  } else {  
      return false;  
  }  
}
if( urlExists('http://www.baidu.com/') ) 
echo "exist";
else echo 'no';
```
# WordPress 
###### pprint_r function 显示Object中全部内容
```
function pprint_r($arrs, $die = false) {
	$bt = debug_backtrace();
	$caller = array_shift($bt);
	echo '<pre style="padding:25px;clear:both;">';
	echo '<h3 style="font-weight:bold;">*Debugging Code* Line:'.$caller['line'].' in '.$caller['file'].': by jinhui.</h3>';
	if(!empty($arrs)) {
		print_r($arrs);
	} else {
		echo 'Oooooops, It\'s Empty ...';
	}
	echo '</pre>';
	
	if($die) {
		die();
		exit();
	}
}
```
```
pprint_r($post);  
$meta = get_post_meta($post->ID, '',true);
```

### wp_mail  邮件
```
$to = "rfd3344@gmail.com";
$subject = "One Order is completed";
$content = "<h1>asdda</h1>";
$headers = array('Content-Type: text/html; charset=UTF-8');
$status = wp_mail($to, $subject, $content, $headers );
```


### 判断是不是 'administrator'
```
global $current_user;
if(in_array('administrator', $current_user->roles )){	
    echo 'administrator';
}
``` 

### Home Page
```
<?php echo get_home_url(); ?>  
```
# OOP – Object Oriented Programming
```
class phpClass{
  var $var1;
  var $var2 = "constant string";
  function myfunc ($arg1, $arg2){
  }
}
```
## construct    构造函数
###### 初始化函数
```
function __construct( $par1, $par2 ) {
   $this->url = $par1;
   $this->title = $par2;
}
```
## destruct析构函数
###### 对象结束其生命周期时（例如对象所在的函数已调用完毕
```
function __destruct() {
print "销毁 " . $this->name . "\n";
}
```
## Extends  继承 

## Public, Protected, Privite 访问权限
```
class MyClass
{   public $public = 'Public';
    protected $protected = 'Protected';
    private $private = 'Private';
    function printHello()
    {   echo $this->public;
        echo $this->protected;
        echo $this->private;
    }
}
$obj = new MyClass();
echo $obj->public; // 这行能被正常执行
echo $obj->protected; // 这行会产生一个致命错误
echo $obj->private; // 这行也会产生一个致命错误
$obj->printHello(); // 输出 Public、Protected 和 Private

/*******    Define MyClass2     ******/
class MyClass2 extends MyClass
{ 
// 可以对 public 和 protected 进行重定义，但 private 而不能
    protected $protected = 'Protected2';
    function printHello()
    {   echo $this->public;
        echo $this->protected;
        echo $this->private;
    }
}
$obj2 = new MyClass2();
echo $obj2->public; // 这行能被正常执行
echo $obj2->private; // 未定义 private
echo $obj2->protected; // 这行会产生一个致命错误
$obj2->printHello(); // 输出 Public、Protected2 和 Undefined
```
# Form 
## Get
    $_Get

# Others 
Data()
date("Y-m-d");


## Include, Require 
##### Include:  Warning错误发生后继续执行，及时包含文件丢失
    include 'header.php';
Require:  Error  错误发生后停止执行，较常使用
## Cocckie 
```
setcookie(name, value, expire, path, domain);
$_COOKIE
$_COOKIE["user"];
```
## Define 自定义常量 
define ( string $name , mixed $value [, bool $case_insensitive = false ] )
case_insensitive   // 可选，为true时大小写不敏感

```
define("ABCDEF ", "BBBBBBBBB");  
echo ABCDEF;    	// BBBBBBBBB
define("ABCDEF ", " BBBBBBBBB ", true);  // 大小写不敏感
echo abcdef;    // BBBBBBBBB
```

# Flasky
Initial
source venv/bin/activate 

pip install flask 
pip install flask-script 
pip install flask-bootstrap 
pip install flask-moment 
                 http://momentjs.com/docs/#/displaying/ 
pip install flask-wtf 
pip install flask-sqlalchemy 
pip install flask-migrate 
pip install flask-mail
pip install flask-login 

pip freeze >requirements.txt        // generate the required files	
pip install -r requirements.txt     //  install  requirements

# Python
   单行注释
render_template传递全部变量
	return render_template('index.html', **locals())
URL:  统一资源定位符		
## Decorator
Foo = hello(foo)     等同于：


for num in range(10,20)    #  from 10 to 20
## If 
if num == 3:            # 判断num的值
    print ( "boss")
else:
    print 'roadman'

## File process
f = open(file_name,"a")
f = write ()
## import argparse
	Parser = argparse.ArgumentParser()
Parser = add_argument('name', help = 'that is the help sentence')
	
## import re
re.match(' think ', line, re.M|re.I )
re.search()


## From threading import Thread
Import timer
thread.join()      #  wait the thread done

#数据结构













