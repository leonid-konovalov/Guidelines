### General guidelines

* Follow the next sets of principles:
    * [SOLID](https://en.wikipedia.org/wiki/SOLID)
    * [GRASP](https://en.wikipedia.org/wiki/GRASP_(object-oriented_design))

* Also, follow the next principles:
    * [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
    * [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it)

* Apply [GoF patterns](https://en.wikipedia.org/wiki/Design_Patterns) when
  suitable

* [Write first, optimize later](
  https://martinfowler.com/ieeeSoftware/yetOptimization.pdf
  )

### Classes

With a few exceptions (such as factories), keep classes small:

* Not more than 100 lines (excluding comments) is ideal
* Between 100 and 200 lines is acceptable
* More than 200 lines should be refactored

### Members

* Unless a few exceptions, make class members private

### Methods

* Keep methods small
    * Not more 10 lines is ideal
    * Between 10 and 32 lines (fits on a screen) is acceptable
    * More than 32 lines must be refactored
* Make the separation between intention and implementation. If effort needed
  to figure out 'what' a fragment of code is doing, extract it into a method
  and name it after 'what'.
* Make class methods private if they are not used outside of the class

### References

* Robert Martin.
  *Agile Software Development, Principles, Patterns, and Practices*.
  1st Edition.
  Pearson, 2002.

* Craig Larman.
  *Applying UML and Patterns: An Introduction to Object-Oriented Analysis and
  Design and Iterative Development*.
  3rd Edition.
  Pearson, 2004.

* Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides.  
  *Design Patterns: Elements of Reusable Object-Oriented Software*.
  1st Edition.
  Addison-Wesley Professional, 1994.

* Martin Fowler.
  *Refactoring: Improving the Design of Existing Code*.
  2nd Edition.
  Addison-Wesley Professional, 2018.
