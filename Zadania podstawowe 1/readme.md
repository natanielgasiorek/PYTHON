## Zadania podstawowe część pierwsza.

#### 1. Napisz program, który pyta użytkownika (input) o imię oraz wiek a następnie wyświetla napisy: Cześć (imię)! Twoje imię ma (liczba liter imienia) liter i zaczyna się od (pierwsza litera imienia) Teraz masz (wiek) lat, a za rok będzie to (wiek za rok). Rok urodzenia to (rok urodzenia).

```
import datetime

# Parametry brane od użytkownika
name = input("Proszę podaj swoje imię: ")
age = input("Proszę podaj swój wiek: ")

# Przebieg programu
length = len(name) #długość stringa
first_letter = name[0] #pierwsza litera imienia

age = int(age)
age_next_year = age + 1

year_now = datetime.datetime.now().year #rok teraz
year_birth = year_now - age #rok urodzenia

# Wyświetl podane informacje
print("Cześć", name)
print("Twoje imię ma", length, "liter i zaczyna się od", first_letter)
print("Teraz masz", age,"lat, a za rok będzie to " + str(age_next_year) + ". Rok urodzenia to", year_birth)

```

![image](https://github.com/natanielgasiorek/PYTHON/assets/91785152/268f934c-5135-4fcc-b38d-482d0f7e51a4)

#### 2. Zapytaj użytkownika o wiek oraz ilość pieniędzy w portfelu. Następnie dokonaj sprawdzenia, czy użytkownik może kupić w sklepie alkohol o wartości 20 zł. Rozpatrz wszystkie 4 przypadki, z których tylko jeden spełnia warunek “jesteś pełnoletni i masz wystarczającą ilość pieniędzy”. Wyświetl stosowną informację dla każdego z przypadków, podając też informację, ile brakuje (w portfelu oraz do pełnoletniości).

```
from decimal import Decimal
# Parametry brane od użytkownika
age = input("Podaj swój wiek: ")
wallet = Decimal(input("Podaj ilość pieniędzy w swoim portfelu (w PLN): "))

# Przebieg programu
def change_years(years):
    if years == 1:
        return f"{years} rok"
    elif 2 <= years % 10 <= 4 and (years % 100 < 10 or years % 100 >= 20):
        return f"{years} lata"
    else:
        return f"{years} lat"

alcohol_price = Decimal("20.0")  #Przyjmujemy, że cena alkoholu wynosi 20 zł
wallet = Decimal(wallet)
age = int(age)

if wallet < alcohol_price:
    lack = alcohol_price - wallet
    
if age < 18:
    years = 18 - age

if age < 18 and wallet < alcohol_price: #1 Jesteś niepełnoletni i nie masz funduszy
    print("Jesteś niepełnoletni! Do pełnoletności brakuje Ci " + str(change_years(years)) + ". Brakuje Ci też", lack, "zł. do pełnej kwoty.")
elif age >= 18 and wallet < alcohol_price: #2 Jesteś pełnoletni ale nie masz funduszy
    print("Jesteś pełnoletni ale brakuje Ci", lack, "zł. do pełnej kwoty.")
elif age < 18 and wallet >= alcohol_price: #3 Jesteś niepełnoletni ale masz fundusze
    print("Jesteś niepełnoletni! Do pełnoletności brakuje Ci " + str(change_years(years)) + ". Masz wystarczające fundusze aby kupić alkohol o wartości", alcohol_price, "zł.")
else: #4. jesteś pełnoletni i masz fundusze
    print("Jesteś pełnoletni i masz wystarczające fundusze aby kupić alkohol o wartości", alcohol_price, "zł.")
```

![image](https://github.com/natanielgasiorek/PYTHON/assets/91785152/0d320e58-6c2e-450a-9174-3b59413d3e98)

#### 3. Napisz prosty kalkulator podatkowy dla podatku dochodowego. Najpierw program niech zapyta użytkownika, czy chce podać dochód miesięczny czy roczny. W przypadku wybrania dochodu miesięcznego oblicz dochód roczny. Następnie na podstawie podanych wartości oblicz wartość rocznego podatku dochodowego w oparciu o I i II próg podatkowy (12% i 32%) - sposób obliczania podatku według progów podatkowych znajdziesz w Internecie. Pomiń kwestie kwoty wolnej od podatku oraz założeń Polskiego Ładu.

```
try:
    choice = input("Czy chcesz podać dochód miesięczny czy roczny? Wpisz 'm' lub 'r': ").lower()
    
    if choice == 'm':
        monthly_income = float(input("Podaj dochód miesięczny: "))
        annual_revenue = monthly_income * 12
    elif choice == 'r':
        annual_revenue = float(input("Podaj dochód roczny: "))
    else:
        print("Błędny wybór. Wpisz 'm' lub 'r'.")
        exit()
        
    # Oblicz podatek na podstawie próg I (12%)
    if annual_revenue <= 120000:
        tax = 0.12 * annual_revenue - 3600
    else:
        # Oblicz podatek na podstawie prógu II (32%)
        tax = 0.32 * (annual_revenue - 120000) + 10800

    print(f"Podatek dochodowy 2023/2024 roku wynosi: {tax} zł.")
        
except error:
    print("Błędne dane. Wprowadź liczbę.")
```
                                                                               
#### 4. Zaprogramuj uproszczoną kasę fiskalną. Najpierw poproś użytkownika jednym wywołaniem input() o wpisanie produktów oddzielonych przecinkiem. Następnie dla każdego produktu (rozdziel je korzystając z funkcji poznanych dla stringów, a następnie stwórz z nich zbiór, aby zapewnić, że nie będą się powtarzać) poproś o wpisanie jego ceny i zapisz wszystko w postaci słownika. Na koniec wyświetl wszystkie elementy słownika w postaci “produkt:cena”.

```
# Parametry brane od użytkownika
products_input = input("Wprowadź produkty oddzielone przecinkiem: ")

products = [product.strip() for product in products_input.split(',')] #Usówamy ewentualne białe znaki

prices_products = {}

# Poproś użytkownika o cenę dla każdego produktu
for product in products:
    if product not in prices_products: # Usówamy duplikaty w ten sposób, wolałem stworzyć listę zamiast używać set.
        price = float(input(f"Podaj cenę dla produktu '{product}': "))
        prices_products[product] = price
    
# Wyświetl produkty w formie "produkt: cena"
for product, price in prices_products.items():
    print(f"{product}: {price} zł")
```

#### Napisz programy, które pobierają od użytkowników odpowiednie liczby (input), a następnie wywołują funkcję, która obliczy: a. pole trójkąta o bokach a,b,c (skorzystaj ze wzoru Herona: https://www.matmana6.pl/wzor-herona)

```
import math

# Funkcja HERONA
def area_triangle_heron(a, b, c):
    
    def half_c(a, b, c):
        
        p = (a + b + c)
        
        return p
     
    p = half_c(a, b, c)
    area = math.sqrt(p * (p - a) * (p - b) * (p - c))    
        
    return area

# Przebieg programu
try:
    a = float(input("Podaj długość boku a: "))
    b = float(input("Podaj długość boku b: "))
    c = float(input("Podaj długość boku c: "))
    
    if a > 0 and b > 0 and c > 0:
        area = area_triangle_heron(a, b, c)
        print(f"Pole trójkąta o bokach {a}, {b} i {c} wynosi: {area}")
    else:
        print("Długości boków muszą być dodatnie.")
        
except ValueError:
    print("Błędne dane. Wprowadź poprawne liczby.")
```
