```markdown
# Strategy Design Pattern in Java

Strategy design pattern allows us to define a family of algorithms, encapsulate each one of them, and make them interchangeable. In this example, we'll implement different payment methods using the Strategy pattern.
```
```
public interface PaymentStrategy {
    void pay(int amount);
}
```

```
public class CreditCardPayment implements PaymentStrategy {
    private String cardNumber;
    private String name;

    public CreditCardPayment(String cardNumber, String name) {
        this.cardNumber = cardNumber;
        this.name = name;
    }

    @Override
    public void pay(int amount) {
        System.out.println("Paid " + amount + " using credit card: " + cardNumber);
    }
}

public class PayPalPayment implements PaymentStrategy {
    private String email;

    public PayPalPayment(String email) {
        this.email = email;
    }

    @Override
    public void pay(int amount) {
        System.out.println("Paid " + amount + " using PayPal account: " + email);
    }
}

public class BitcoinPayment implements PaymentStrategy {
    private String bitcoinAddress;

    public BitcoinPayment(String bitcoinAddress) {
        this.bitcoinAddress = bitcoinAddress;
    }

    @Override
    public void pay(int amount) {
        System.out.println("Paid " + amount + " using Bitcoin address: " + bitcoinAddress);
    }
}

```

```
import java.util.ArrayList;
import java.util.List;

public class ShoppingCart {
    private List<Item> items;
    
    public ShoppingCart() {
        items = new ArrayList<>();
    }

    public void addItem(Item item) {
        items.add(item);
    }

    public int calculateTotal() {
        int total = 0;
        for (Item item : items) {
            total += item.getPrice();
        }
        return total;
    }

    public void checkout(PaymentStrategy paymentStrategy) {
        int totalAmount = calculateTotal();
        paymentStrategy.pay(totalAmount);
    }
}

```

```
public class Main {
    public static void main(String[] args) {
        ShoppingCart cart = new ShoppingCart();
        cart.addItem(new Item("Item 1", 50));
        cart.addItem(new Item("Item 2", 30));

        PaymentStrategy creditCardPayment = new CreditCardPayment("1234-5678-9012-3456", "John Doe");
        PaymentStrategy paypalPayment = new PayPalPayment("john@example.com");
        PaymentStrategy bitcoinPayment = new BitcoinPayment("1A2B3C4D5E6F7G8H9I");

        // Use different payment strategies
        cart.checkout(creditCardPayment);
        cart.checkout(paypalPayment);
        cart.checkout(bitcoinPayment);
    }
}


```