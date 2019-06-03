#                         Data Structure Reference

## C++ Basics

<strong>Introduction:</strong>
C++ is a Superset of C. If you know syntax of C language then it is easy cup of tea. C++ is
Object Oriented Programming language. It has features like Object, Class, Inheritance, Polymorphism
etc.C++ is more powerful than any other language like Java, Python etc. It is more closer to
hardware so you can take advantage of every bit of resources.

## Separation of Interface and Implementation
##### IntCell class interface in file IntCell.h
```
#ifndef IntCell_H
#define IntCell_H
/**
* A class for simulating an integer memory cell.
*/
class IntCell
{
public:
explicit IntCell( int initialValue = 0 );
int read( ) const;
void write( int x );
private:
int storedValue;
};
#endif
```

##### IntCell class implementation in file IntCell.cpp
```
#include "IntCell.h"
/**
* Construct the IntCell with initialValue
*/
IntCell::IntCell( int initialValue ) : storedValue{ initialValue }
{
}
/**
* Return the stored value.
*/
int IntCell::read( ) const
{
return storedValue;
}
/**
* Store x.
*/
void IntCell::write( int x )
{
storedValue = x;
}
```
##### main function included class IntCell.cpp

```
#include <iostream>
#include "IntCell.h"
using namespace std;
int main( )
{
IntCell m;
m.write( 5 );
cout << "Cell contents: " << m.read( ) << endl;
return 0;
}
```
### Pointers
```
int main( )
{
IntCell *m;  // * indicates it is a pointer variable
m = new IntCell{ 0 };  // new allocates the memory to pointer variable... it is initialValue
m->write( 5 );
cout << "Cell contents: " << m->read( ) << endl;
delete m;  // delete flush the memory location of variable.
return 0;
}
````

### Parameter passing:
#### Call by value -
```
double average( double a, double b );
// returns average of a and b
double z = average( x, y );  // Call by value.
```
#### Call by Reference -
```
void swap( double & a, double & b );
// swaps a and b;
swap( x, y );  // this is reference based call.
```

##### Note:
1. Call-by-value is appropriate for small objects that should not be altered by the
function.
2. Call-by-constant-reference is appropriate for large objects that should not be altered
by the function and are expensive to copy.
3. Call-by-reference is appropriate for all objects that may be altered by the function.

### Function Template
A function template is not an actual function, but instead is a pattern for what could
become a function.

##### findMax function template
```
/**
* Return the maximum item in array a.
* Assumes a.size( ) > 0.
* Comparable objects must provide operator< and operator=
*/
template <typename Comparable>
const Comparable & findMax( const vector<Comparable> & a )
{
int maxIndex = 0;
for( int i = 1; i < a.size( ); ++i )
if( a[ maxIndex ] < a[ i ] )
maxIndex = i;
return a[ maxIndex ];
}

```
#   Analysis of Algorithm
Many time solution is found but it does not gives performance as required. so
As name suggest here we are Analysis to time and resources used by our Algorithm.

##### Some Important Pointers
###### Typical Growth Rate:

```
Function      Name
c             Constant         
log N         Logarithmic
log^2 N       Log-squared
N             Linear
N log N         
N^2           Quadratic
N^3           Cubic
2^N           Exponential

```
![image](/DS_runningTime.png);

Another one :
![image2](/DS_runningTime.png);

You can see the result briefly...

### Running Time Calculation
<strong>Rule 1: For Loop</strong>
Running time is O(N).
<strong>Rule 2: Nested For Loop</strong>
Running time is O(N^2).
<strong>Rule 4—If/Else</strong>
For the fragment
if( condition )
S1
else
S2

Running time is : O(N);



## List, Stacks and Queues

### Abstract Data type
An abstract data type (ADT) is a set of objects together with a set of operations.
Objects such as lists, sets, and graphs,
along with their operations, can be viewed as ADTs, just as integers, reals, and booleans are
data types. Integers, reals, and booleans have operations associated with them, and so do
ADTs.

<strong>The list ADT</strong>
        /          \
 Simple array       Simple Linked
implementation        List.

<strong>Please Note:</strong>
Both vector and list are class templates that are instantiated with the type of items
that they store. Both have several methods in common. The first three methods shown are
actually available for all the STL containers:
r int size( ) const : returns the number of elements in the container.
r void clear( ) : removes all elements from the container.
r bool empty( ) const : returns true if the container contains no elements,
and false
otherwise.
Both vector and list support adding and removing from the end of the list in constant
time. Both vector and list support accessing the front item in the list in constant time.
The operations are:
r void push_back( const Object & x ) : adds x to the end of the list.
r void pop_back( ) : removes the object at the end of the list.
r const Object & back( ) const : returns the object at the end of the
list (a mutator that
returns a reference is also provided).
r const Object & front( ) const : returns the object at the front of the list (a mutator that
returns a reference is also provided).
Because a doubly linked list allows efficient changes at the front, but a vector does not,
the following two methods are available only for list :
r void push_front( const Object & x ) : adds x to the front of the list .
r void pop_front( ) : removes the object at the front of the list .
The vector has its own set of methods that are not part of list . Two methods allow
efficient indexing. The other two methods allow the programmer to view and change the
internal capacity. These methods are:
r Object & operator[] ( int idx ) : returns the object at index idx in the vector , with no
bounds-checking (an accessor that returns a constant reference is also provided).
r Object & at( int idx ) :
returns the object at index idx in the vector , with bounds-
checking (an accessor that returns a constant reference is also provided).
r int capacity( ) const :
returns the internal capacity of the vector . (See Section 3.4 for
more details.)
r void reserve( int newCapacity ) :
sets the new capacity. If a good estimate is available,
it can be used to avoid expansion of the vector .

### Iterator
#### Getting an Iterator
For the first issue, the STL lists (and all other STL containers) define a pair of methods:
r iterator begin( ) :
returns an appropriate iterator representing the first item in the
container.
r iterator end( ) :
returns an appropriate iterator representing the endmarker in the
container (i.e., the position after the last item in the container).

```
for( int i = 0; i != v.size( ); ++i )
cout << v[ i ] << endl;
```
If we were to rewrite this code using iterators, we would see a natural correspondence
with the begin and end methods:
```
for( vector<int>::iterator itr = v.begin( ); itr != v.end( ); itr. ??? )
cout << itr. ??? << endl;
```
