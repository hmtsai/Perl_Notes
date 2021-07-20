One of eval usage is for trapping error without causing the whole program stops.

```eval { expression1; exprression2; ...};```

Inside the eval block {}, if one of the expression cause fatal error, the error message is stored in the variable $@.
if all expression behaves good. the return value of the eval block is the result of the last expression.

```Perl
$a = 10;
$b = 20;
$c = 30;
$d = 40;
$ret = eval {
    $a = 1;
    $b = 0;
    $c = $a/$b;
    $d = 3;
};
warn $@ if ($@);        # eval: store the error message in $@ 
print "$a $b $c $d\n";
print "1st ret: $ret \n";   # eval: the return value is the result of last expression 

$ret = eval {
    $a = 1;
    $b = 2;
    $c = $a/$b;
    $d = 3;
};
warn $@ if ($@);        # eval: store the error message in $@ 
print "$a $b $c $d\n";
print "2nd ret: $ret \n";   # eval: the return value is the result of last expression 

```

* Result
```
$perl main.pl
1 0 30 40
1st ret:  
1 2 0.5 3
2nd ret: 3 
Illegal division by zero at main.pl line 11.
```
