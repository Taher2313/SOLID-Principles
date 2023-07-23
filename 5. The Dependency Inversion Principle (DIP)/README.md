# The Dependency Inversion Principle

The Dependency Inversion principle states that our classes should depend upon interfaces or abstract classes instead of concrete classes and functions.



We want our classes to be open to extension, so we have reorganized our dependencies to depend on interfaces instead of concrete classes. Our PersistenceManager class depends on InvoicePersistence instead of the classes that implement that interface.



## Example that shows DIP violation

![](https://github.com/Taher-Mohamed-Ahmed-Saad/SOILD-Principles/blob/main/Images/3.png)

## Solve the violation using interface

![](https://github.com/Taher-Mohamed-Ahmed-Saad/SOILD-Principles/blob/main/Images/4.png)

