# F3 PhpStorm Snippets


[Fat-Free Framework](https://github.com/bcosca/fatfree) snippets for [PhpStorm](http://www.jetbrains.com/phpstorm/).

## How-To install
to install PhpStorm schemes, settings and templates, you need to find its user config folder first. This should be present at:

+ Windows: `<your home directory>\.PhpStorm<version>\config\`
+ Linux: `~\.PhpStorm<version>\config\`
+ MacOS: `~/Library/Preferences/PhpStorm<version>/`


## Code Style

The F3 code style uses a very compact alignment. 

To install, copy `codestyles/F3_Codestyle.xml` to your config folder. If the `codestyles` directory does not exist, just create it. Restart PhpStorm and continue at Preferences > Editor > Code Style 

* set default right margins (columns) to 90 (no exceptions)
* select F3 Scheme
* apply
	
when you now use your Menu > Code > Reformat Code, it should be all formatted in decent F3 style, oh yeah ;)


## Live-Template

To install, copy the `templates/F3.xml` file to your user config folder. If the `templates` directory does not exist, just create it.
Now restart PhpStorm and check if the F3 LiveTemplate is checked in the settings.

![Settings](http://ikkez.de/linked/F3-Snippets-Settings.jpg)


### Usage

Now you can write the following keywords, hit your `TAB` key and let the magic begin. Some snippets have multiple variables to be filled. Hit your `ENTER` key to proceed to the next input section.

Check out this little demo:

![Demo](http://ikkez.de/linked/f3-snippets-demo.gif)


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

All template snippets are using the namespaced tags with a `F3:` prefix like the tag `<F3:repeat ... >`. This is helpful, since PhpStorm will colorize this in your html markup, so you'll find it easier to spot the F3 parts in your templates.

---

#### {{

``` html
{{  }}
```

#### {-

exclude an expression (useful for JS-variables)

``` html
{-{{  }}-}
```

#### {~

exclude a part (do not echo it)

``` html
{~  ~}
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
<F3:check if="{{ @ }}">

</F3:check>
```

#### true

To extend the check section with true and false parts.

``` html
<F3:true>

</F3:true>
<F3:false>

</F3:false>
```

#### switch

``` html
<F3:switch expr="{{ @ }}">
    <F3:default> </F3:default>
    <F3:case value=" "> </F3:case>
    <F3:case value=" "> </F3:case>
</F3:switch>
```

#### case

adds an additional case with break option to a switch section

``` html
<F3:case value=" " break="true"> </F3:case>
```

#### include

``` html
<F3:include href=" " />
```

#### includeif

``` html
<F3:include if="{{ @ }}" href=" " />
```


#### loop

``` html
<F3:loop from="{{ @i=0 }}" to="{{ @i < count(@bar) }}" step="{{ @i++ }}">
        	
</F3:loop>
```

#### repeat

``` html
<F3:repeat group="{{ @array }}" value="{{ @val }}">
    {{ @val }}
</F3:repeat>
```

#### repeat kv

expands to: repeat with key and value

``` html
<F3:repeat group="{{ @array }}" key="{{ @key }}" value="{{ @val }}">
  {{@key}} {{@val}}
</F3:repeat>
```

#### repeat vc

expands to: repeat with value and counter

``` html
<F3:repeat group="{{ @array }}" value="{{ @val }}" counter="{{ @i }}">
{{@i}}: {{@val}}
</F3:repeat>
```

#### repeat kvc

expands to: repeat with key, value and counter

``` html
<F3:repeat group="{{ @array }}" key="{{ @key }}" value="{{ @val }}" counter="{{ @i }}">
{{@i}}: {{@key}} {{@val}}
</F3:repeat>
```

#### set

``` html
<F3:set key="value" />
{{@key}}
```


