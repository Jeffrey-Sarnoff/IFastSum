## IFastSum
Correctly rounded floating point summation for arbitrary length vectors that do not overflow.  
```ruby
                                                      Jeffrey Sarnoff © 2016-Mar-22 at New York
```
This implements IFastSum from "Some Highly Accurate Basic Linear Algebra Subroutines" by Yuhang Zhao (c) 2010.  
I have introduced two minor changes:  

       If the intermediate summand overflow, Inf is returned (Zhao's version terminates on overflow).  
       Round3 is reimplemented using reinterpret; this is somewhat faster than Zhao's Round3.  

### Use
```julia
using IFastSum

v = rand(9_876_543)
s = iFastSum(v)  # if !isinf(s) then s is the correctly rounded sum

```

### Performance
I benchmark iFastSum(v) 30x faster than sum(b)   
where b=[BigFloat(x) for x in v] using setprecision(120 or 256)

### Note
In the event of overflow, you can use vs = sort(v,lt=lessthanMag); iFastSum(vs)  
  which is not going to overflow spuriously, but is dominated by the sort time.
