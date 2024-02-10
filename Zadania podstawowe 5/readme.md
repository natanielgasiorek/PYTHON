### 2. (1pkt) Napisz klasę BankAccount, która będzie reprezentować konto bankowe. Konto powinno mieć pola publiczne (np. numer, waluta) oraz prywatne
(np. saldo, wlaściciel). Stwórz gettery i settery pozwalające na dostęp do wartości prywatnych (bez dekoratorów!). Dodaj magic methods, które pozwolą
na wydrukowanie danych konta w upiększonej postaci (str), obliczenie "długości" konta (czyli jego stanu) oraz dodanie do siebie salda dwóch kont, pod
warunkiem, że są z tego samego banku, w tej samej walucie i tego samego właściciela. Stwórz obiekt i przetestuj działanie wszystkich metod.

```
#2
class BankAccount:
    def __init__(self, number, currency, balance, owner):
        self.number = number
        self.currency = currency
        self._balance = balance
        self._owner = owner  

    def get_balance(self):
        return self._balance

    def get_owner(self):
        return self._owner


    def set_balance(self, new_balance):
        self._balance = new_balance

    def set_owner(self, new_owner):
        self._owner = new_owner

    def __str__(self):
        return f"Account {self.number} owned by {self._owner} with balance {self._balance} {self.currency}"

    def __len__(self):
        return self._balance

    def __add__(self, other):
        if isinstance(other, BankAccount) and \
                self.number == other.number and \
                self.currency == other.currency and \
                self._owner == other._owner:
            new_balance = self._balance + other.get_balance()
            return BankAccount(self.number, self.currency, new_balance, self._owner)
        else:
            print("cannot add accounts")

# Przykład użycia
account1 = BankAccount("123456", "USD", 1000, "user1")
account2 = BankAccount("123456", "USD", 1500, "user2")

print(account1)
print(len(account1))

new_account = account1 + account2
print(new_account)

```
### 3. (1pkt) Zmodyfikuj stworzoną klasę BankAccount, używając dekoratorów do zrobienia gettera i settera. Dodaj metodę statyczną
convert_currency(amount, exchange_rate), który pozwoli na konwersję kwoty z jednej waluty na inną.

```
#3
class BankAccount:
    def __init__(self, number, currency, balance, owner):
        self.number = number
        self.currency = currency
        self._balance = balance  # saldo jako pole prywatne
        self._owner = owner  # właściciel jako pole prywatne

    # Getter i setter dla _balance
    @property
    def balance(self):
        return self._balance

    @balance.setter
    def balance(self, new_balance):
        self._balance = new_balance

    # Getter i setter dla _owner
    @property
    def owner(self):
        return self._owner

    @owner.setter
    def owner(self, new_owner):
        self._owner = new_owner

    # Metody magiczne
    def __str__(self):
        return f"Account {self.number} owned by {self._owner} with balance {self._balance} {self.currency}"

    def __len__(self):
        return self._balance

    def __add__(self, other):
        if isinstance(other, BankAccount) and \
                self.number == other.number and \
                self.currency == other.currency and \
                self._owner == other._owner:
            new_balance = self._balance + other.balance
            return BankAccount(self.number, self.currency, new_balance, self._owner)
        else:
            raise ValueError("Accounts cannot be added. Make sure they belong to the same owner, bank, and have the same currency.")

    # Metoda statyczna do konwersji waluty
    @staticmethod
    def convert_currency(amount, exchange_rate):
        return amount * exchange_rate

# Przykład użycia
account1 = BankAccount("123456", "USD", 1000, "John Doe")
account2 = BankAccount("123456", "USD", 1500, "John Doe")

# Ustawienie nowego salda za pomocą settera
account1.balance = 2000
print(account1.balance)  # Wyświetlenie nowego salda

# Ustawienie nowego właściciela za pomocą settera
account1.owner = "Jane Doe"
print(account1.owner)  # Wyświetlenie nowego właściciela

# Wywołanie metody statycznej do konwersji waluty
converted_amount = BankAccount.convert_currency(100, 0.85)
print(f"Converted amount: {converted_amount} EUR")
```
### 4. (1pkt) Napisz generator haseł, z wykorzystaniem yield. Na wejściu funkcji podaj liczbę znaków, dodaj też opcję minimalnej liczby liter i minimalnej
liczby cyfr (moduł string) jako parametry z wartościami domyślnymi. Następnie wygeneruj w ten sposób 5 haseł z ustalonymi warunkami.

```
#4
import string
import random

def generate_password(length, min_letters=1, min_digits=1):
    while True:
        password = ''.join(random.choice(string.ascii_letters) for _ in range(min_letters))
        password += ''.join(random.choice(string.digits) for _ in range(min_digits))
        password += ''.join(random.choice(string.ascii_letters + string.digits) for _ in range(length - min_letters - min_digits))
        
        password_list = list(password)
        random.shuffle(password_list)
        yield ''.join(password_list)

# Przykład użycia
password_generator = generate_password(length=8, min_letters=2, min_digits=2)

for _ in range(5):
    generated_password = next(password_generator)
    print(generated_password)

```
