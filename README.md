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
