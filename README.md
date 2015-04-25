#Template::Protone 

Creating synergy throughout the world by bringing harmonious designs and interfaces into a collaborative space that resides between what users want and also giving people what they need.

Also, a templating system that allows you to embed perl6.  ```EVAL```s your templates into a callable sub and caches them for later use, if you want.

#Usage

```perl6
use Template::Protone;

my Template::Protone $templ .= new;

$templ.parse(template => [q|
Hello <% print "WORLD!"; %>

Oh, did you want variables too?  I can do <% print $data<what>; %> too.

<% for ^3 { %>
<% print $_ ~ ($_ == 2 ?? '' !! ', '); %>
<% } %>
|], :name<example>);

say $templ.render(:name<example>, :data(what => 'that'));
```

##Output

```
Hello WORLD!

Oh, did you want variables too?  I can do that too.

0, 1, 2
```

#What's that?  You don't like <% and %> ?

```perl6
qw<...>;

use Template::Protone;

my Template::Protone $templ .= new(:open('%%'), :close("%%"));

say $templ.render(template => [q|
Hello %% print "WORLD!"; %%

List: %% for ^3 {  
   print $_ ~ ($_ == 2 ?? '' !! ', '); 
 } %%
|]);

qw<...>;
```

##Output
```
Hello WORLD!

List: 0, 1, 2
```
