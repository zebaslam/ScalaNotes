A pure oo language is one in which every value is an object

* Boolean maps to JVM primitive type boolean

Two principal forms of polymorphism

* **subtyping**: pass instances of subtype where base class was required
* **generics**: parameterize types with other types

Type Bounds
===========

Consider the method assertAllPos which

* takes an IntSet
* returns an IntSet if all elements are positive
* throws an exception otherwise
* `​def assertAllPos(s: IntSet): IntSet`

* ​Howver this doesnt fully express all cases such as Empty set =\> Empty set or NonEmpty =\> NonEmpty

* Better way of expressing this:

* `​def assertlAllPos[S <: IntSet](r:S) : S = …`
* ​Here the “`<: IntSet`” is an upper bound of the type parameter S

* This means that S can be instantiated only to types that conform to IntSet

* Generally, the notation

* `S <: T `means S is a subtype of T
* `S >: T `means S is a supertype of T (or T is a subtype of S)

Lower Bounds
------------

* `S >: NonEmpty `​

* Introduces a type parameter S that can range only over supertypes of NonEmpty
* S could be: NonEmpty, IntSet, AnyRef or Any

Mixing Lower and Upper Bounds
-----------------------------

* `​[S >: NonEmpty <: IntSet]`​

* This would restrict S any type on the interval between NonEmpty and IntSet

Covariance
----------

**Covariance: **Subtyping varies with type parameter.

