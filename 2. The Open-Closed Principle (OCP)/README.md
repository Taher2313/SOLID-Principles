# 2. The Open-Closed Principle

The Open-Closed Principle requires that **classes should be open for extension and closed to modification.**

Modification means changing the code of an existing class, and extension means adding new functionality.

So what this principle wants to say is: We should be able to add new functionality without touching the existing code for the class. This is because whenever we modify the existing code, we are taking the risk of creating potential bugs. So we should avoid touching the tested and reliable (mostly) production code if possible.

This principle can be applied using abstract classes or interfaces.

## Example that shows OCP violation

Assume that we have class InvoicePersistence and we need to add the functionality to save to DB not only file.

Before modification

```java
public class InvoicePersistence {
    Invoice invoice;

    public InvoicePersistence(Invoice invoice) {
        this.invoice = invoice;
    }

    public void saveToFile(String filename) {
        // Creates a file with given name and writes the invoice
    }
}
```

After modification

```java
public class InvoicePersistence {
    Invoice invoice;

    public InvoicePersistence(Invoice invoice) {
        this.invoice = invoice;
    }

    public void saveToFile(String filename) {
        // Creates a file with given name and writes the invoice
    }

    public void saveToDatabase() {
        // Saves the invoice to database
    }
}
```

here we changed in a class that is already working and tested.

## Solve the violation using interface

Here we create interface so any new features can be added to the overridden functions.

![](https://github.com/Taher-Mohamed-Ahmed-Saad/SOILD-Principles/blob/main/Images/1.png)

```java
interface InvoicePersistence {

    public void save(Invoice invoice);
}

public class DatabasePersistence implements InvoicePersistence {

    @Override
    public void save(Invoice invoice) {
        // Save to DB
    }
}

public class FilePersistence implements InvoicePersistence {

    @Override
    public void save(Invoice invoice) {
        // Save to file
    }
}
```

Now our persistence logic is easily extendable. If we want to add another database and have 2 different types of databases like MySQL and MongoDB, we can easily do that.
