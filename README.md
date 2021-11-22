# Test2 cheat sheet for Perl developers

[Test2 module from CPAN](https://metacpan.org/pod/Test2)

## SYNOPSIS

```
use Test2::V0;

is( $got, $expect, $name, @diag );
```

## Audience

**Do you want to use Test2 to test your code?**

 - start: [Test2::Suite](https://metacpan.org/pod/Test2::Suite)
 - user docs: [Test2::Tools::Compare](https://metacpan.org/pod/Test2::Tools::Compare)

**Do you want to extend the Test2 framework itself?**

 - see: [Test2::API](https://metacpan.org/pod/Test2::API)
 - maintenance docs: [Test2::Compare](https://metacpan.org/pod/Test2::Compare)

## Compare

TODO:
```
use Test2::Tools::Compare qw{
    match mismatch validator
    hash array bag object meta number float rounded within string subset bool
    in_set not_in_set check_set
    item field call call_list call_hash prop check all_items all_keys all_vals all_values
    etc end filter_items
    event fail_events
    exact_ref
};
```

### is

```
is(
    $some_hash,
    hash {
        field a => 1;
        field b => match(qr/[0-9]+/);
    },
    "message"
);
```

### isnt

```
isnt( $got, $expect, $name );
```

### like

```
like(
    $some_hash,
    {
        a => 1,
        b => qr/[0-9]+/,
    },
    "message"
);
```

### unlike

```
unlike( $got, $expect, $name );
```

### T

Assert the value is true.

```
is( $foo, T(), '$foo has a true value' );
```

### F

Assert the value is false. And that the key exists, if used in a hash

```
is($foo, F(), '$foo exists (if key in hash) and has a false value');
```

### D

Assert the value is defined.

```
is('foo', D(), 'foo is defined');
```

### U

Assert the value is undefined.

```
is(undef, U(), 'not defined');
```

### DF

Assert the value is defined and false.

is(0, DF(), 'foo is defined but false');

### E

Assert the value exists in an array, or key exists in a hash.

```
is( ['a', 'b', undef], ['a', 'b', E() ], "There is a third item in the array" );
is( {a => 1, b => 2}, {a => 1, b => E() }, "The 'b' key exists in the hash") ;
```

### DNE

Assert the value does not exist, or check end bound of an array.

```
is( ['a', 'b'], ['a', 'b', DNE()], "There is no third item in the array" );
is( {a => 1}, {a => 1, b => DNE()}, "The 'b' key does not exist in the hash" );
```

### FDNE

Combination of F() and DNE().

```
check = FDNE();
```

### L

Assert value is defined and has non-zero length.

```
$check = L();
```

## Misc

### Target

```
Test2::V0 -target => 'Foo::Bar';

$CLASS->do_something();
```

### Rename/multiple targets

```
use Test2::V0 -target => { ROLE => 'Some::Role' };
# ...
DOES_ok( $class, [$ROLE], "$class does $ROLE" );
```

