# Designing for Perfomance
> Martin Thompson

## Performance
Has been growing 2x/year since the 60's, but slow down and gone backwards recently with Spectre/Meltdown

Ensure you have overhead, so you can add features without worrying. Ensure there is capacity

Excess logging will slow things down almost every time

DRY can often lead to unneccessary abstration that leads to very tight coupling

Polymorphism and megamorphism can often lead to poor performance. Compilers have issues have 4 or 5

Law of leaky abstraction: The underlying complexity cannot be ignored

Design classes with memory allocation in mind. Properties that can be changed and accessed together should be in a class together

Code branches (`for`, `while`, `if`) are slow and CPU's are not optemised to handle these

Compilers are good at inlining. Let them do their thing

Performant code isn't complicated code. Simple code is often more performant than complex code 