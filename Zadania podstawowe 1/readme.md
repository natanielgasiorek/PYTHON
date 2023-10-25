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
