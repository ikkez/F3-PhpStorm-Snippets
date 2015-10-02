# F3 PhpStorm Snippets


[Fat-Free Framework](https://github.com/bcosca/fatfree) snippets for [PhpStorm](http://www.jetbrains.com/phpstorm/).

## How-To install

to install, copy the `F3.xml` file to:

+ Windows: `<your home directory>\.WebIde<version>\config\templates`
+ Linux: `~\.WebIde<version>\config\templates`
+ MacOS: `~/Library/Preferences/WebIde<version>/templates` (for 9.x versions)

Now restart PhpStorm and check if the F3 LiveTemplate is checked in the settings.

![Settings](https://dl.dropboxusercontent.com/u/3077539/_linked/F3-Snippets-Settings.jpg)

## Usage

Now you can write the following keywords, hit your `TAB` key and let the magic begin. Some snippets have multiple variables to be filled. Hit your `ENTER` key to proceed to the next input section.

Check out this little demo:

![Demo](https://dl.dropboxusercontent.com/u/3077539/_linked/F3-Snippets-Demo.gif)

### PHP Snippets

#### base

expands to:

``` php
/** @var \Base $f3 */
$f3 = \Base::instance();
```


#### route

``` php
$f3->route('GET /','Class->method');
```

#### route function

``` php
$f3->route('GET /',function( Base $f3, $params) {
    
});
```

#### db_jig

``` php
$f3->set('DB', new \DB\Jig('data/'));
```

#### db_mongo

``` php
$f3->set('DB', new \DB\Mongo('mongodb://localhost:27017', 'testdb'));
```

#### db_mysql

``` php
$f3->set('DB', new \DB\SQL('mysql:host=localhost;port=3306;dbname=fatfree', 'fatfree', 'fatfree'));
```

#### db_pgsql

``` php
$f3->set('DB', new \DB\SQL('pgsql:host=localhost;dbname=fatfree', 'fatfree', 'fatfree'));
```

#### db_sqlsrv

``` php
$f3->set('DB', new \DB\SQL('sqlsrv:Server=localhost,1433;Database=fatfree', 'fatfree', ''));
```

#### db_sqlite

``` php
$f3->set('DB', new \DB\SQL('sqlite:data/sqlite.db'));
```


### Template Snippets


#### {{

``` html
{{  }}
```

#### @

``` html
{{ @var }}
```

#### @?

a shortcut to print a variable, if it has been defined.

``` html
{{isset(@var)?@var:''}}
```

#### @esc

``` html
{{ @var | esc }}
```


#### @raw

``` html
{{ @var | raw }}
```


#### check

A check with true-only section

``` html
<check if="{{ @ }}">

</check>
```

#### true

To extend the check section with true and false parts.

``` html
<true>

</true>
<false>

</false>
```

#### switch

``` html
<switch expr="{{ @ }}">
    <default> </default>
    <case value=" "> </case>
    <case value=" "> </case>
    
</switch>
```

#### case

adds an additional case with break option to a switch section

``` html
<case value=" " break="true"> </case>
```

#### include

``` html
<include if="{{ @ }}" href=" " />
```


#### loop

``` html
<loop from="{{ @i=0 }}" to="{{ @i < count(@bar) }}" step="{{ @i++ }}">
        	
</loop>
```

#### repeat

``` html
<repeat group="{{ @array }}" value="{{ @val }}">
    {{ @val }}
</repeat>
```

#### repeat kv

expands to: repeat with key and value

``` html
<repeat group="{{ @array }}" key="{{ @key }}" value="{{ @val }}">
  {{@key}} {{@val}}
</repeat>
```

#### repeat vc

expands to: repeat with value and counter

``` html
<repeat group="{{ @array }}" value="{{ @val }}" counter="{{ @i }}">
{{@i}}: {{@val}}
</repeat>
```

#### repeat kvc

expands to: repeat with key, value and counter

``` html
<repeat group="{{ @array }}" key="{{ @key }}" value="{{ @val }}" counter="{{ @i }}">
{{@i}}: {{@key}} {{@val}}
</repeat>
```

#### set

``` html
<set key="value" />
{{@key}}
```

---

Template snippets can also be accessed with the `f3` prefix, i.e. like `f3repeat`, which will create the tag `<F3:repeat ... >`. 
