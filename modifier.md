* /x : dont care white space.

  so if you want to match with space, you need specifiy it exactly, e.g., /s*
* /m : multiline match.
 
  you have to specify ^ for match begin of a line.
* /s : match any character including '\n'

  if you want match some pattern which is crossing \n
* /i : ignoare Upper or Lower case 

  dont care it is Upper/Lower case.
```Perl
#
# Hello World Program in Perl
#
print "Hello World!\n";

my $ms = <<"EOS";
first line
second line
EOS
# use marker "EOS" to declare multiline string. 
# or my $ms = "first line\nsecond line";

print $ms;

if ( $ms =~ /first.*second/s ) {
    print "with /s : matched \n";
} else {
    print "not matched \n";
}

if ( $ms =~ /^second/m ) {
    print "with /m : ^second matched \n";
} else {
    print "not matched \n";
}

if ( $ms =~ /first\s*line/x ) {
    print "with /x : first\\s*line matched \n";
} else {
    print "not matched \n";
}
print "=========\n";
if ( $ms =~ /first.*second/ ) {
    print "matched \n";
} else {
    print "without /s : not matched \n";
}

if ( $ms =~ /^second/ ) {
    print "matched \n";
} else {
    print "without /m : ^seocnd not matched \n";
}

if ( $ms =~ /first line/x ) {
    print "matched \n";
} else {
    print "with /x : first line not matched \n";
}
```
* Result
```
$perl main.pl
Hello World!
first line
second line
with /s : matched 
with /m : ^second matched 
with /x : first\s*line matched 
=========
without /s : not matched 
without /m : ^seocnd not matched 
with /x : first line not matched 
```
