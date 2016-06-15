We are creating a small interpreter for arithmetic expressions restricted to numbers and additions. Expressions can be represented by a class heirarchy with a base trait Expr and two subclasses Number and Sum.

```scala
trait Expr {
  def isNumber: Boolean
  def isSum: Boolean
  def numValue : Int
  def leftOp: Expr
  def rightOp: Expr
}

class Number(n: Int) extends Expr {
  def isNumber: Boolean = true
  def isSum: Boolean = false
  def numValue : Int = n
  def leftOp: Expr = throw new Error("Number.leftOp")
  def rightOp: Expr = throw new Error("Number.rightOp")
}
```

Next we want to examine creating a Sum class as a subclass of Expr where Sum can be expressed as follows:

`​new Sum(e1, e2) = e1 + e2`

```

```

```scala
class Sum(e1: Expr, e2: Expr) extends Expr {
  def isNumber: Boolean = false
  def isSum: Boolean = true
  def numValue: Int = throw new Error("Sum.numValue")
  def leftOp: Expr = e1
  def rightop: Expr = e2
}
```

We want eval to be used like this: ​eval(Sum(Number(1), Number(2))) = 3

We can now right an evaluation function as follows:

```scala
def eval(e:Expr): Int {
  if (e.isNumber) e.numValue
  else if(e.isSum) eval(e.leftOp) + eval(e.rightOp)
  else throw new Error("Unknown expression " + e)
}
```

