## IFastSum.jl
Correctly rounded floating point summation for arbitrary length vectors that do not overflow.  

This implements IFastSum from "Some Highly Accurate Basic Linear Algebra Subroutines" by Yuhang Zhao (c) 2010.  
I have introduced two minor changes:  

  -- If the intermediate summand overflow, NaN is returned (Zhao's version terminates on overflow).  
  -- Round3 is reimplemented using reinterpret; this is somewhat faster than Zhao's Round3.  

