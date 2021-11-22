# Test2 cheat sheet for Perl developers

[Test2 module from CPAN](https://metacpan.org/pod/Test2)

## SYNOPSIS

```
use Test2::V0;


```

## Navigation

  - regular users of Test2 (i.e. developers of other code) --> start at [Test2::Suite](https://metacpan.org/pod/Test2::Suite) and find user docs under Test2::Tools::\* namespace, e.g. [Test2::Tools::Compare](https://metacpan.org/pod/Test2::Tools::Compare)

  - if you want to extend the Test2 framework itself, i.e. write a new _type_ of test --> see [Test2::API](https://metacpan.org/pod/Test2::API) and the lower-level library docs, e.g. [Test2::Compare](https://metacpan.org/pod/Test2::Compare) (yes, it's confusing)

## Compare

TODO:
```
use Test2::Tools::Compare qw{
    is like isnt unlike
    match mismatch validator
    hash array bag object meta number float rounded within string subset bool
    in_set not_in_set check_set
    item field call call_list call_hash prop check all_items all_keys all_vals all_values
    etc end filter_items
    T F D DF E DNE FDNE U L
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
        field b => 2;
        field c => 3;
    },
    "Hash matches spec"
);
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

