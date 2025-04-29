# Avoid Template Method

That's it. That's the whole article.

Okay, I'll explain a bit more.

## What is Template Method ?

Template Method is the name of a behavioral design pattern that was first described if the GoF book. It aims at factoring
out common behaviors when different workflows share a similar structure and enabling specific implementation differences.

More specifically, Template Method uses inheritance to achieve this. An abstract base class defines the template alongside
protected methods that inheriting classes can override to suit their specific needs.

Here is an example implementation of the pattern for a transaction processor where the main workflow consists in processing
a transaction, and specific details vary depending on the medium used.

```typescript
abstract class FinancialTransactionProcessor<PAYMENT_MEDIUM_DATA> {
  public processTransaction(transactionId: string, amount: number, mediumData: PAYMENT_MEDIUM_DATA): Promise<void> {
    if (!this.authorize(mediumData)) {
      throw new Error('Authorization Failed');
    }

    if (!this.process(amount, data)) {
      throw new Error('Processing Failed');
    }

    this.recordSuccess(transactionId);
    this.notify();
  }

  // Abstract methods that must be implemented by all workflows
  protected abstract authorize(data: PAYMENT_MEDIUM_DATA): boolean;
  protected abstract process(amount: number, data: PAYMENT_MEDIUM_DATA): boolean;

  // Not all workflows implement notification, so we have a default implementation
  protected notify() {
    console.log('Notification not implemented for this transaction type');
  }

  // Private method that is only defined by the parent class
  private recordSuccess(id: string): void {
    console.log(`Saving successful transaction: ${id}`)
  }
}
```

Now, let's define the medium-specific workflows:

```typescript
interface CreditCard {
  cardNumber: string;
}

class CreditCardProcessor extends FinancialTransactionProcessor<CreditCard> {
  protected authorize(data: CreditCard): boolean {
    return data.cardNumber === '1234-5678-90';
  }

  protected process(amount: number, data: CreditCard): boolean {
    console.log('Something something credit card magic');
    return true
  }
  
  protected notify() {
    console.log('Hello dear user, 8000$ have been charged to your credit card, have a good day!')
  }
}

interface CryptoWallet {
  walletAddress: string;
}

class CryptocurrencyProcessor extends FinancialTransactionProcessor<CryptoWallet> {
  protected authorize(data: CryptoWallet): boolean {
    return data.walletAddress === "SBF's wallet"
  }

  protected process(amount: number, data: CryptoWallet): boolean {
    console.log(`Only costs an arm in processing fees !`)
    return true;
  }
}
```

## Issues

### Lack of flexibility



## Alternatives
