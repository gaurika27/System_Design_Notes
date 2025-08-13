# What is an Interface?
At its core, an interface defines a contract: a set of method signatures that any implementing class must fulfill. It declares what a class can do, but not how it does it.

In object-oriented design, interfaces play a foundational role in building systems that are extensible, testable, and loosely coupled.

hey allow different parts of the system to interact through well-defined contracts without needing to know how the behavior is actually implemented.

## Real-World Analogy
Consider a remote control. It exposes a standard set of buttons:

 - ```play()```
 - ```pause()```
 - ```volumeUp()```
 - ```powerOff()```

The person using the remote doesn’t care whether it controls a TV, a soundbar, or a projector. The interface remains the same, but the underlying device behaves differently.

This is exactly how interfaces work in software design.

# Key Properties of Interfaces
### Defines behavior without dictating implementation
An interface specifies what operations are expected, but not how they are carried out. This gives freedom to implementers to provide customized logic while still honoring the contract.

### Enables polymorphism
Different classes can implement the same interface in different ways. This allows your code to work with different implementations interchangeably.

### Promotes decoupling
Code that depends on interfaces is insulated from changes in concrete implementations. This reduces the ripple effect of changes and increases testability and maintainability.

# Example: Payment Gateway Interface
Let’s say you’re designing a payment processing module that supports multiple providers like Stripe, Razorpay, and PayPal.

You can define a generic interface:
```C++
class PaymentGateway {
public:
    virtual ~PaymentGateway() {}  // Virtual destructor for proper cleanup
    virtual void initiatePayment(double amount) = 0;  // Pure virtual function
};
```
This interface doesn’t care how the payment is processed—it only mandates that all implementing classes must define a method called ```initiatePayment()```.

Now you can create multiple implementations:
```C++
class StripePayment : public PaymentGateway {
public:
    void initiatePayment(double amount) override {
        cout << "Processing payment via Stripe: $" << amount << endl;
    }
};

class RazorpayPayment : public PaymentGateway {
public:
    void initiatePayment(double amount) override {
        cout << "Processing payment via Razorpay: ₹" << amount << endl;
    }
};
```
Both ```StripePayment``` and ```RazorpayPayment``` implement the same interface, but the actual logic for processing the payment is different.

### Usage: Loose Coupling in Action
Now let’s say you have a CheckoutService that processes payments. Instead of hardcoding a specific payment gateway, you inject the interface:
```C++
class CheckoutService {
private:
    PaymentGateway* paymentGateway;

public:
    CheckoutService(PaymentGateway* gateway) : paymentGateway(gateway) {}
    
    void setPaymentGateway(PaymentGateway* gateway) {
        paymentGateway = gateway;
    }
    
    void checkout(double amount) {
        if (paymentGateway != nullptr) {
            paymentGateway->initiatePayment(amount);
        }
    }
};
```
Now you can plug in any payment gateway at runtime:
```C++
int main() {
    StripePayment stripeGateway;
    CheckoutService service(&stripeGateway);
    service.checkout(120.50);  // Output: Processing payment via Stripe: $120.5
    
    // Switch to Razorpay
    RazorpayPayment razorpayGateway;
    service.setPaymentGateway(&razorpayGateway);
    service.checkout(150.50);  // Output: Processing payment via Razorpay: ₹150.5
  
    return 0;
}
```

No change required in ```CheckoutService```
