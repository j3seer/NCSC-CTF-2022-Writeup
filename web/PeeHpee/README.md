# Challenge description

Dali likes PhP because it's weird and has a lot of bugs. Is that really true ?
Link: http://20.119.58.135:1234

**Author: Kahla**

-----------------------------------------------------------

we were provided this php source code

```php

<?php
//Show Page code source
highlight_file(__FILE__);
require "secret.php";
if(isset($_GET["__"])&&isset($_GET["_"])){
$x=$_GET["__"];
$inp=preg_replace("/[^A-Za-z0-9$]/","",$_GET["_"]);
if($inp==="Kahla"){
    die("Hacking Attempt detected");
}
else{
    if(eval("return $inp=".$inp.";")==="Kahla"){
        echo $flag;
    }
    else{
        die("Pretty Close maybe ?");
    }
}
}
?>

```

trying to send **"Kahla"** in the **_** param prints out this prompt

Payload : ``` http://20.119.58.135:1234/?__=&_=Kahla; ``` 

Output : ```Hacking Attempt detected```

We notice that we have the other **__** param too that we haven't trie to use yet 
and it seems sorta useless but its there soo we might as well just use it right?

So we know that the code is filtering the word **Kahla** and won't allow us to get the flag with it 
so how about we use the **__** to send it to the **_** param? since it's not verifying that param

Payload : ``` http://20.119.58.135:1234/?__=Kahla&_=$_GET[__] ```

Output : img

well i guess we're pretty close :/ ?
We can't use the **GET** to send the param because the regex won't allow the [] characters 
But notice that we have a **$x** variable in the source code that takes the **__** value !!
all we need to do is just to pass that through the **_** param

Payload : ``` http://20.119.58.135:1234/?__=Kahla&_=$x ```

Output : ``` Securinets{PeehPee_1s_AlWAYs_H3r3} ```

And there's our flag!




