# Projekt: Coffe Shop - analiza

## 1. Opis projektu

Projekt Power BI służy do analizy sprzedaży produktów w różnych sklepach. Raport pozwala na śledzenie kluczowych wskaźników, takich jak wartość sprzedaży, rentowność, liczba transakcji oraz analiza sezonowości.

Odbiorcy raportu: Zarząd, dział sprzedaży, analitycy biznesowi.

# Kluczowe pytania biznesowe:

- Jakie są trendy sprzedażowe w ujęciu miesięcznym i rocznym?

- Które produkty przynoszą największy zysk?

- Jak wygląda sezonowość sprzedaży?

- Jaki jest udział poszczególnych kategorii produktowych w sprzedaży?

## 2. Źródła danych

- Baza danych sprzedażowa (SQL Server / Excel / API)

- Kalendarz jako tabela pomocnicza

- Dodatkowe pliki CSV z kategoriami produktów

- Dane są ładowane w trybie importu.

## 3. Model danych
# Relacje między tabelami:
![image](https://github.com/user-attachments/assets/4a77de08-be28-4234-9ec7-f0fc317432c6)

# Struktura tabel:
# Produkty

- Produkt ID

- Nazwa produktu

- Kategoria

- Rodzaj produktu

- Rozmiar

- Zawiera mleko

- Zawiera orzechy

# Sprzedaż

- Data zamówienia

- Data księgowania

- ID Zamówienia

- Sklep ID

- Produkt ID

- Liczba jednostek

- Cena jednostkowa

- Cena zakupu

- Wartość sprzedaży

- Koszt

- Zysk
