## part 1. what to write in .h and .cpp

| header files (.h) | non-template                                                                                                                     | temlate                                                                                                                   |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
|                   | * global variable declaration (extern) <br/>        * global function declaration <br/>     * global function (inline) definition <br/>         | * template global function (inline) declaration and definition <br/>                                                            |
|                   | * class definition <br/>  * class member functions and data members definition * static const data member initialization inside class | * template class definition  <br/> * class member declaration and definition   (definition can be inside or outside the class) |
| .cpp files        | * global variable definition (and initialization) <br/>  * global function definition                                                 | N/A                                                                                                                       |
|                   | * class member function definition  <br/> * static data member initialization                                                         | N/A                                                                                                                       |
|                   |                                                                                                                                  |                                                                                                                           |

## part 2. examples
Assume that you are implementing a matrix class using vector<vectors<double>>. The file matrix.h looks like:  
```
#ifndef MAT_H    
#define MAT_H  
#include <something>
using namespace std;
class mat {
    friend mat function_A(const mat2&,const mat2&);//purpose of func
    friend mat function_B(const mat2&,double n);//purpose of func
      ... ... ... ... ... ... ... ..
public:
    //constructor
    ... ... ... 
    //member functions
    //shape() -- return a tuple contain the row and col;
      ... implementations...
    //a member func to return the transpose of itself
    mat transpose() {
     ... implementations
    }
private:
    unsigned rows,cols;
    vector<vector<double> > matrix;//the rows and columns of the matrix;

};
//all declarations outside class
mat funcs(some_type, some_type);

#endif //
```
  
And the mat.cpp file contains all detailed implementations, looks like:
```
#include "mat.h"

mat dot(const mat& a,const mat& b) {
    /* the purpose and comments of the func : 
    Arguments:
    a -- const mat, a matrix
    b -- const mat, another matrix
    Return:
    tmp -- inner product of a and b
    */
     .. implementations...
 
```

