In the book "Learning Perl", the list and array are defined clearly.
> A list is an ordered collection of scalars. An array is a variable that contains a list. People tend to use the terms interchangeably, but there’s a big difference. The list is the data and the array is the variable that stores that data. You can have a list value that isn’t in an array, but every array variable holds a list (although that list may be empty).

```Perl
@a = ( 1, "ab" ); # 'a' is a array. 
                  # (1, "ab") is a list.
                  # you can other syntax with qw "quote word":  
                  #    @a = qw /1 ab/;     
                  # or @a = qw {1 ab};

@b = @a;    # b is a copy from a
$c = \@a;   # c is a reference to a
            # if you swap a's elements, b is not changed but c (since it is a reference)

print "@a \n";
print "@b \n";
print "@$c \n";
print "$c->[0] $c->[1]\n";
print "after swap ===============\n";
($a[0], $a[1]) = ($a[1], $a[0]);
print "@a \n";
print "@b \n";
print "@$c \n";
```
* Result
```
1 ab 
1 ab 
1 ab 
1 ab
after swap ===============
ab 1 
1 ab 
ab 1 
```

* array in another array

use [ ] inside another array to *represent reference of the inside array*.
[a, b] is a reference of the list (a, b).

```Perl
@arr = ( [a, b], 
         333 );

$s = @arr[0];
print "$s \n";       # $s is scaler stored the reference of the list (a, b) 
print "@$s[1] \n";
print "$s->[1]\n";
print "$\@arr[0]->[1] \n";
print "$arr[1] \n";
```
* Result
```
ARRAY(0xbb9950) 
b 
b
b 
333 
```
