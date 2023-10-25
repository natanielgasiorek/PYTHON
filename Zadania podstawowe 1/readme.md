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
                                                                               
#### 4. Zaprogramuj uproszczoną kasę fiskalną. Najpierw poproś użytkownika jednym wywołaniem input() o wpisanie produktów oddzielonych przecinkiem. Następnie dla każdego produktu (rozdziel je korzystając z funkcji poznanych dla stringów, a następnie stwórz z nich zbiór, aby zapewnić, że nie będą się powtarzać) poproś o wpisanie jego ceny i zapisz wszystko w postaci słownika. Na koniec wyświetl wszystkie elementy słownika w postaci “produkt:cena”.

