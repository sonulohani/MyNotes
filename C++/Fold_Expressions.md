With C++11 we got variadic templates which is a great feature, especially if you want to work with a variable number of input parameters to a function. For example, previously (pre C++11) you had to write several different versions of a function (like one for one parameter, another for two parameters, another for three params... ).

Still, variadic templates required some additional code when you wanted to implement 'recursive' functions like `sum`, `all`. You had to specify rules for the recursion:

For example:

```cpp
auto SumCpp11(){
    return 0;
}

template<typename T1, typename... T>
auto SumCpp11(T1 s, T... ts){
    return s + SumCpp11(ts...);
}
```

And with C++17 we can write much simpler code:

```cpp
template<typename ...Args> auto sum(Args ...args) 
{ 
    return (args + ... + 0); 
}

// or even:

template<typename ...Args> auto sum2(Args ...args) 
{ 
    return (args + ...);
}
```

Fold expressions over a parameter pack.


|Expression   |Expansion   |
|---|---|
| (... op pack)  | ((pack1 op pack2) op ...) op packN  |
| (init op ... op pack)  | (((init op pack1) op pack2) op ...) op packN  |
|  (pack op ...) | pack1 op (... op (packN-1 op packN))  |
|  (pack op ... op init) | pack1 op (... op (packN-1 op (packN op init)))  |

Also by default we get the following values for empty parameter packs:

|Operator   |Default value   |
|---|---|
| &&  | true  |
| &#8739;&#8739;  | false  |
|  , | void()  |

Here's quite nice implementation of a printf using folds [P0036R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf):

```cpp
#include <iostream>
#include <string>

using namespace std;
 
template<typename ...Args>
void FoldPrint(Args&&... args) {
    (cout <<  ... <<  forward<Args>(args)) << '\n';
}

int main()
{
    FoldPrint("hello", ", ", 10, ", ", 90.0);
}
```

Or a fold over a comma operator:

```cpp
template<typename T, typename... Args>
void push_back_vec(std::vector<T>& v, Args&&... args)
{
    (v.push_back(args), ...);
}
```

Push back and folds:

```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;
 
template<typename T, typename... Args>
void FoldPushBack(vector<T>& v, Args&&... args)
{
    (v.push_back(args), ...);
}

int main()
{
    vector<int> v;
	FoldPushBack(v, 1, 2, 3, 4);
	
	for (auto &i : v)
		cout << i << "\n";
}
```

In general, fold expression allows writing cleaner, shorter and probably easier to read code.
