# Projekt: Coffe Shop - analiza

## 1. Opis projektu

Projekt Power BI służy do analizy sprzedaży produktów w różnych sklepach. Raport pozwala na śledzenie kluczowych wskaźników, takich jak wartość sprzedaży, rentowność, liczba transakcji oraz analiza sezonowości. Dodatkowo umożliwia identyfikację najbardziej dochodowych produktów, lokalizacji oraz sezonowych trendów sprzedaży. Dzięki dynamicznym filtrom użytkownicy mogą dostosować analizę do swoich potrzeb i uzyskać szczegółowe informacje na temat sprzedaży w różnych ujęciach.

Odbiorcy raportu: 

- Zarząd,
  
- Dział sprzedaży,
  
- Analitycy biznesowi.

### Kluczowe pytania biznesowe:

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
### Relacje między tabelami:
![image](https://github.com/user-attachments/assets/4a77de08-be28-4234-9ec7-f0fc317432c6)

### Struktura tabel:
#### Produkty

- Produkt ID

- Nazwa produktu

- Kategoria

- Rodzaj produktu

- Rozmiar

- Zawiera mleko

- Zawiera orzechy

#### Sprzedaż

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

#### Sklepy

- Sklep ID

- Miasto

- Miasto Skrót

- Adres

- Kod Pocztowy

- Województwo

- Wielkość miasta

- Segment miasta

#### Kalendarz

- Date

- Dzień

- Nr. dnia tygodnia

- Dzień tygodnia

- Nr. tygodnia

- Nr. miesiąca

- Miesiąc

- Kwartał

- Rok

- Rok miesiąc

- Rok miesiąc numer

- Początek miesiąca

- Koniec miesiąca

- Czy weekend
  
## 4. Miary DAX

### Podstawowe miary:

- Suma sprzedaży: SUM(Sprzedaz[Wartość sprzedaży])

- Średnia sprzedaż na transakcji:

    DIVIDE(
    [Suma sprzedaży],
    [Liczba transakcji]
    )

- Marża procentowa:

   DIVIDE(
    SUM(Sprzedaz[Zysk]),
    SUM(Sprzedaz[Wartość sprzedaży])
    )
  
-  YoY sprzedaż (rok do roku):
  
    VAR SprzedazObecny = [Suma sprzedaży]
    VAR SprzedzPoprzedni =
        CALCULATE(
          [Suma sprzedaży],
          SAMEPERIODLASTYEAR(Kalendarz[Date])
        )
  RETURN
      DIVIDE(SprzedazObecny - SprzedzPoprzedni, SprzedzPoprzedni, 0)

- Liczba produktów: DISTINCTCOUNT(Produkty[Produkt ID])

- Produkty zawierające mleko:

    CALCULATE( 
      [Liczba produktów],
      Produkty[Zawiera mleko] = "tak"
      )

- Sprzedaż YTD: TOTALYTD([Suma sprzedaży], Kalendarz[Date])

- Sprzedaż MTD: TOTALMTD([Suma sprzedaży], Kalendarz[Date])

## 5. Raporty i wizualizacje

### Strony raportu:

- Home - strona wstępna

- Przegląd sprzedaży - główne wskaźniki KPI, trend sprzedaży, marża i sprzedaż 

- Analiza produktów - sprzedaż według kategorii, top produkty, MTD, YTD.

- Drzewo dekompozycji - indeks sezonowości, sprzedaż w ujęciu miesięcznym.
  
### Kluczowe wizualizacje:

- Wykres liniowy sprzedaży miesięcznej

- Ranking top N produktów

- Wskaźniki KPI (marża, rentowność, liczba transakcji)
  
## 6. Reguły i standardy

- Nazewnictwo miar: używamy polskich nazw, np. "Suma sprzedaży".

- Formatowanie wartości: wartości walutowe w złotówkach, procenty z dwoma miejscami po przecinku.

## 7. Instrukcja użytkowania raportu

- Użytkownicy mogą korzystać z filtrów (np. według miasta, produktu, daty) w celu dostosowania widoku raportu.
  
- Kliknięcie w konkretny element raportu (np. produkt, sklep) wyświetla szczegółowe dane związane z wybranym elementem.
  
## 8. Administracja i utrzymanie
 
- Osoba odpowiedzialna: Katarzyna Tondaś, Analityk BI

- Monitorowanie błędów: logowanie problemów w SharePoint.

- Optymalizacja wydajności: regularne sprawdzanie miar DAX i optymalizacja zapytań.


