---
layout: post
title:  "4 things you will learn to use with perl"
date:   2018-01-27 21:55:35 -0200
categories: Tech Inside
---

**Just like any other language, Perl will teach you a couple of things;**

## 1. [Pattern matching](https://perldoc.perl.org/perlre.html#The-Basics) is awesome and is **EVERYWHERE**:
	
##### easily you can find out this kind of syntax to import! Packages;
```
use if scalar (SERVER_VAR =~ m/^(service_a|service_b)$/), 'Object::Db::Model' => qw( Admin );
```
	
##### or to get check for matches;
	
```
my $match = '10-123-2-1245' =~ m/(\d{3,})/;
my $match_2 = '10-1-2-1' =~ m/(\d{3,})/;
print $match?1:0,"\n";
print $match_2?1:0,"\n";
```
**output:**	
	
```
1
0
[Finished in 0.1s]
```
	
##### Getting the first match
```
my ($match) = '10-123-2-1245' =~ m/(\d{3,})/;
print $match,"\n";
```
**output:**

```
123
[Finished in 0.1s]
```
	
##### get all mathes? just include `g`
	
```
my @match = '10-123-2-1245' =~ m/(\d{3,})/g;
print join ',',@match,"\n";
```
	
**output:**
```
123,1245,
[Finished in 0.1s]
```
	
##### use with variables? no problem
```
my $email = '(\d{3,})';
my $a = '10-123-2-1245' =~ m/$email/;
```
	
	
## 2. Punctuation variables -> [perlvar](https://perldoc.perl.org/perlvar.html):
	
Perl has already built in variables; <br/>
**I love to write as less as possible to reach my goal. This kind of struture helps me a lot!**
	
**After knowing it's hard to stop using:**
For instance:
	
```
my @a = (1,2,3,4);
for (@a){
	print $_,"\n";
}
```
	
**output**
```
1
2
3
4
[Finished in 0.1s]
```
	
Specially if you uses a lot [SYSTEM variables] (https://perldoc.perl.org/perlvar.html#General-Variables), now this will be Handy;
	
```
%ENV
$PROGRAM_NAME
$PID
$GID
$REAL_USER_ID	
```
	
## 3. [References and types](https://perldoc.perl.org/perlintro.html#Perl-variable-types) 
	
In perl you will understand that the less is more. In most of case you will only lead with **3 different types**, and it's **ok**.<br/> 
Of course you can implement all *fancy stuff as Object Orientations guide lines.*<br/>
With perl you can start coding and delievering real value with those simples strutures.
	
```
# Perl has 3 basic (natives) types: ($,@,%)
my $scalar_val = 1;
my @array_val = [1,2,3,4,5,6];
my %hash_val = (1,2,3,4,5,6);
# can be also declared as 
my $hash_val = {1=>2,3=>4,5=>6}; 
```
	
## 4. [Map,](http://perldoc.perl.org/functions/map.html) [Sort,](http://perldoc.perl.org/functions/sort.html) [Grep,](http://perldoc.perl.org/functions/grep.html) and arrays and hashes:

One of best ways to improve your script is understanding the best way to use hashes; With perl this is extremely intuitive.
	
##### HOW USE MAP?
	
**MAP** is an operation that will implement the function over your array. In most case you can use `for`.
For instance:
	
```
my @av = (1,2,3,4,5,6);
print join ',', @av,"\n";
@av = map {$_*2} @av;
print join ',', @av,"\n";
```
**output:**

```
1,2,3,4,5,6,	
2,4,6,8,10,12,
[Finished in 0.1s]
```
	
#### HOW USE GREP?
	
**GREP** works same as filter over the array. For instance:

```	
my @av = (1,2,3,4,5,6);
print join ',', @av,"\n";
@av = grep {$_%2} @av;
print join ',', @av,"\n";
```
**output:**
	
```
1,2,3,4,5,6,
1,3,5,
[Finished in 0.1s]
```
	
#### HOW USE SORT?
	
**SORT** is very handy no great change from grep or map; As you already are using `$_`, for **SORT** you need to use `$a` and `$b` and [`<=>` or `CMP`](https://perldoc.perl.org/perlop.html#Equality-Operators)  operators. For instance:
	
	
```	
my @av = (4,2,1,5,3,0);
print join ',', @av,"\n";
@av = sort {$a <=> $b} @av;
print join ',', @av,"\n";
```
**output:**
	
```
1,2,3,4,5,6,
1,3,5,
[Finished in 0.1s]
```
	
### HOW TO CONVERT ARRAY TO HASH
just a FYI
	
```
my @av = (4,2,1,5,3,0);
my $v = { map { $_=>1} @av};
print Dumper($v),"\n";
```
	
**output:**
	
```
$VAR1 = {
      '2' => 1,
      '4' => 1,
      '1' => 1,
      '0' => 1,
      '3' => 1,
      '5' => 1
    };
	
[Finished in 0.1s]
```
	
