# Projekt: Coffe Shop - analiza

## 1. Opis projektu

Projekt Power BI ma na celu szczegółową analizę sprzedaży produktów w różnych lokalizacjach sieci Coffee Shop. Raport umożliwia monitorowanie kluczowych wskaźników, takich jak wartość sprzedaży, rentowność, liczba transakcji oraz analiza sezonowości. Dodatkowo, raport pozwala na identyfikację najbardziej dochodowych produktów, lokalizacji oraz sezonowych trendów sprzedaży. Dzięki dynamicznym filtrom użytkownicy mogą dostosować analizę do swoich potrzeb i uzyskać szczegółowe informacje na temat sprzedaży w różnych ujęciach.

Odbiorcy raportu: 

- Zarząd - potrzebuje strategicznych informacji do podejmowania decyzji dotyczących rozwoju sieci sklepów oraz optymalizacji oferty produktowej.
  
- Dział sprzedaży - skupia się na operacyjnych aspektach sprzedaży, takich jak monitorowanie wyników sprzedaży, identyfikacja najlepszych praktyk oraz planowanie działań promocyjnych.
  
- Analitycy biznesowi - analizują dane w celu identyfikacji trendów, anomalii oraz możliwości optymalizacji procesów biznesowych.

### Kluczowe pytania biznesowe:

- Jakie są trendy sprzedażowe w ujęciu miesięcznym i rocznym? Analiza trendów pozwala na zrozumienie, jak sprzedaż zmienia się w czasie, co może pomóc w planowaniu przyszłych działań.
  
- Które produkty przynoszą największy zysk? Identyfikacja najbardziej dochodowych produktów pozwala na optymalizację oferty oraz skoncentrowanie działań marketingowych na tych produktach.
  
- Jak wygląda sezonowość sprzedaży? Analiza sezonowości pomaga w zrozumieniu, w jakich okresach sprzedaż jest najwyższa, co może wpłynąć na planowanie zapasów oraz kampanii promocyjnych.
  
- Jaki jest udział poszczególnych kategorii produktowych w sprzedaży? Pozwala to na ocenę, które kategorie produktów są najważniejsze dla biznesu i gdzie warto inwestować.

## 2. Źródła danych

- Baza danych sprzedażowa (SQL Server / Excel / API) - główne źródło danych zawierające szczegółowe informacje o transakcjach sprzedaży.

- Kalendarz jako tabela pomocnicza - umożliwia analizę danych w kontekście czasowym, co jest kluczowe dla analizy trendów i sezonowości.

- Dodatkowe pliki CSV z kategoriami produktów - uzupełniają dane sprzedażowe o informacje dotyczące kategorii produktów, co pozwala na bardziej szczegółową analizę.

Dane są ładowane w trybie importu, co zapewnia szybki dostęp do dużych zbiorów danych i umożliwia kompleksową analizę.

## 3. Model danych

### Tabele:
- Produkty: Zawiera informacje o produktach, takie jak nazwa, kategoria, rodzaj, rozmiar oraz informacje o alergenach.
- Sprzedaż: Zawiera szczegółowe dane dotyczące transakcji sprzedaży, takie jak data zamówienia, liczba jednostek, cena jednostkowa, wartość sprzedaży, koszt oraz zysk.
- Sklepy: Zawiera informacje o lokalizacjach sklepów, takie jak miasto, adres, kod pocztowy, województwo, wielkość miasta oraz segment miasta.
- Kalendarz: Zawiera informacje o czasie, takie jak data, dzień tygodnia, miesiąc, kwartał, rok oraz informacje o weekendach.
  
### Schemat relacji między tabelami:
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

- Suma sprzedaży:
  
 ![image](https://github.com/user-attachments/assets/2aceff7b-9844-40a5-8d50-9bde510c7f31)

- Średnia sprzedaż na transakcji:

![image](https://github.com/user-attachments/assets/4570b128-b6e8-4012-982f-2af653c07745)

- Marża procentowa:

![image](https://github.com/user-attachments/assets/63c8dd4e-b352-431b-8365-8aae82612f61)
  
-  YoY sprzedaż (rok do roku):
  
![image](https://github.com/user-attachments/assets/fbb892ce-cb38-46d5-aeec-0e521cd6bc4e)

- Liczba produktów:

![image](https://github.com/user-attachments/assets/954f22e1-5628-4f48-af4c-fb852d26c8a2)

- Produkty zawierające mleko:

![image](https://github.com/user-attachments/assets/1fc12f8f-25c5-4252-80fe-1ec667073660)

- Sprzedaż YTD oraz MTD: 

![image](https://github.com/user-attachments/assets/c67af4d9-a4be-42b5-bbc0-5683645973e4)
      

## 5. Raporty i wizualizacje

### Strony raportu:

- Home - Strona wstępna z wprowadzeniem do raportu.

- Przegląd sprzedaży - Główne wskaźniki KPI, trend sprzedaży, marża i sprzedaż.

- Analiza produktów - Sprzedaż według kategorii, top produkty, MTD, YTD.

- Drzewo dekompozycji - Wizaualizacja dynamiczna, do badania wybranej wielkości: marża, koszty, sprzedaż pod kątem nałożonych przez Użytkownika raportu filtrów.
  
### Kluczowe wizualizacje:

- Wykres liniowy sprzedaży miesięcznej

- Ranking top N produktów

- Wskaźniki KPI (marża, rentowność, liczba transakcji)
  
## 6. Reguły i standardy

- Nazewnictwo miar: używamy polskich nazw, np. "Suma sprzedaży".

- Formatowanie wartości: wartości walutowe w złotówkach, procenty z dwoma miejscami po przecinku.

## 7. Instrukcja użytkowania raportu

- Raport jest interaktywny, umożliwiając użytkownikom dostosowanie widoków za pomocą dynamicznych filtrów.
- Użytkownicy mogą eksplorować dane na różne sposoby, aby uzyskać szczegółowe informacje na temat sprzedaży i podejmować świadome decyzje biznesowe.
- Model danych jest zbudowany w taki sposób, aby istniała możliwość dodawania kolejnych tabel wymiarów, w celu rozszerzenia analizy.
  
## 8. Administracja i utrzymanie
 
- Osoba odpowiedzialna: Katarzyna Tondaś, Analityk danych

- Monitorowanie błędów: logowanie problemów w SharePoint.

- Optymalizacja wydajności: regularne sprawdzanie miar DAX i optymalizacja zapytań.


