# To Do App

**Stan na 07.05.2025 dla wersji To Do 2.20.1**

**Przewidywana data publikacji:** Lipiec 2025

## Spis treści:

1. [Autor](#autor)
2. [Opis projektu](#opis-projektu)
    
    - Opis projektu
    - Cele projektu
    - Zadania aplikacji

3. [Dane aplikacji i użytkownika](#dane-aplikacji-i-użytkownika)

    - Struktura danych
    - Przechowywanie danych
    - Zabezpieczenia

4. [Technologia wykonania projektu](#technologia-wykonania-projektu)
5. [Wersje](#wersje)
6. [Kompatybilność](#kompatybilność)
7. [Wymagania systemowe](#wymagania-systemowe)
8. [Uprawnienia](#wymagane-uprawnienia)
9. [Wykorzystane pakiety NuGet](#wykorzystane-pakiety-nuget)
10. [Licencja](#licencja)
11. [Plan rozwoju]()

## Autor

Autor projektu: Jakub Kowalik

Rozpoczęcie prac nad projektem: Grudzień 2024

[Konto na Githubie](https://github.com/Phoenix4331)

## Opis projektu:
Aplikacja To Do to narzędzie pomocne w organizacji zadań oraz zarządzaniu czasem, zaprojektowane z myślą o prostocie i wydajności. Umożliwia użytkownikom łatwe dodawanie, edytowanie i usuwanie zadań, co pozwala na lepszą organizację dnia pracy.

**Cele projektu**

1. **Ułatwienie organizacji zadań**
    
    Aplikacja ma na celu pomóc użytkownikom w zarządzaniu swoimi zadaniami, umożliwiając łatwe dodawanie, edytowanie, usuwanie oraz śledzenie ich stanu.

2. **Gotowość do implementacji na innych platformach**

    Dzięki zastosowanej technologii MAUI Multi-platform, projekt jest gotowy na wdrożenie na inne platformy

3. **Prosta i intuicyjna obsługa**

    Prosty interfejs z możliwością dostosowania obsługi w ustawieniach aplikacji dla najwyższej wygody użytkowania

4. **Bezpieczeństwo danych dzięki lokalnemu przechowywaniu danych**

    Aplikacja przechowuje dane lokalnie – na urządzeniu użytkownika, co daje pełną kontrolę nad nimi oraz ogranicza ryzyko ich nieautoryzowanego dostępu, utraty lub udostępnienia. Dzięki temu użytkownik ma pewność, że jego dane są przechowywane w bezpieczny sposób, a wszelkie operacje na danych odbywają się bez potrzeby przesyłania ich do zewnętrznych serwerów.


**Zadania aplikacji**

1. Dodawanie zadania
    
    - Umożliwia użytkownikowi dodanie nowego zadania do listy, z określeniem tytułu, opisu, daty i czasu wykonania, notatek zadania oraz priorytetu, a także dostosowaniu podstawowego wyglądu wyświetlanego zadania.

2. Edycja zadania

    - Pozwala użytkownikowi edytować istniejące zadanie, w tym tytuł, opis, notatki, datę, czas, priorytet oraz wygląd.

3. Usuwanie zadania

    - Umożliwia użytkownikowi usunięcie zadania z listy.

4. Dodawanie, usuwanie i modyfikowanie powiadomień

    - Aplikacja wysyła powiadomienia, która ustawia użytkownik. Zarządzanie nimi jest możliwe przez osobny panel powiadomień lub przez kartę szczegółów konkretnego zadania.

5. Eksport oraz import danych

    - Dane przechowywane w aplikacji można łatwo eksportować i importować w celu przeniesienia na nowe urządzenie lub zrobienia kopii zapasowej. Planowane jest też dodanie konwersji tych danych do nowych wersji. Ze względu na różną strukturę danych w różnych wersjach, do tego czasu nie jest możliwe przenoszenie danych między wersjami (więcej o wersjach [tutaj](#wersje)).

## Dane aplikacji i użytkownika:

**Struktura danych**

Każdy obiekt klasy Task zawiera:

- Tytuł (Title) typu String
- Opis (Description) typu String
- Data końcowa zadania (Date) typu DateTime
- Czas wykonania zadania (Time) typu DateTime
- Notatki (Notes) typu String
- Kolor (Color) typu String
- Stan ukończenia (IsDone) typu Bool (*obecnie nieużywane - przygotowane pod rozwój aplikacji*)
- Priorytet (HighPriority) typu Bool
- Kod identyfikacyjny (Id) typu String

**Przechowywanie danych**

Dane o zadaniach przechowywane są lokalnie - na urządzeniu użytkownika w formie plików tekstowych. Należy mieć na uwadze, że dane te nie są szyfrowane, więc w razie przechowywania informacji wrażliwych sugeruje się rozważenie dodatkowych zabezpieczeń telefonu. Więcej na temat zabezpieczeń poniżej oraz w sekcji [Plan rozwoju](#plan-rozwoju).

**Zabezpieczenia**

Obecnie aplikacja nie szyfruje danych przechowywanych lokalnie, ponieważ nie zawierają one informacji wrażliwych, które wymagałyby zaawansowanego poziomu ochrony. Dane wprowadzane przez użytkownika, takie jak zadania, nie wymagają szyfrowania w kontekście przeznaczenia aplikacji, ale użytkownicy powinni być świadomi, że dane są przechowywane w prostym formacie tekstowym. W planach jest wprowadzenie szyfrowania (patrz [Plan rozwoju](#plan-rozwoju))

## Technologia wykonania projektu:

Aplikacja To Do opiera się na technologii Microsoft MAUI Multi-platform z wyłączeniem następujących platform:

- Windows
- MacOS
- iOS
- Tizen

Interfejs aplikacji (UI) został stworzony za pomocą języka znaczników XAML. Logika aplikacji (back-end) napisany jest w języku C#.

Aplikacja oparta jest na platformie [.NET 9.0](https://dotnet.microsoft.com/en-us/).

## Wersje:

Wersje aplikacji nadawane są według wzoru:

>MAJOR.MINOR.PATCH-PRERELEASE_ID

- MAJOR - Wersja główna, duże zmiany, brak możliwości przenoszenia danych między tymi wersjami

    - np. danych importowanych z wersji 2.20a nie można przenieść do wersji 3.00

- MINOR - Nowe funkcje kompatybilne wstecznie w obrębie jednej wersji MAJOR

- PATCH - Poprawki wersji (naprawa błędów i drobne zmiany np. optymalizacyjne)

- PRERELEASE_ID - Dodatkowe oznaczenie występujące w wersjach specjalnych

    - alpha - wersja w fazie testów deweloperskich
    - beta - wersja w fazie otwartych testów
    - rc - gotowa do wydania, sprawdzana pod względem stabilności

**Przykłady**

>2.20.1 - finalna wersja aplikacji

>2.20.1-alpha - wersja deweloperska

>2.20.1-beta - wersja testowa

>2.20.1-rc - gotowa do wydania, ostatecznie testowana

## Kompatybilność:
**Aplikacja jest kompatybilna z:**
- Android 7.0 (API 24 - Nougat)
- Android 7.1 (API 25 - Nougat)
- Android 8.0 (API 26 - Oreo)
- Android 8.1 (API 27 - Oreo)
- Android 9.0 (API 28 - Pie)
- Android 10.0 (API 29)
- Android 11.0 (API 30)
- Android 12.0 (API 31)
- Android 12.1 (API 32)
- Android 13.0 (API 33)
- Android 14.0 (API 34)
- Android 15.0 (API 35)

**Aplikacja zoptymalizowana do wersji Android 15.0 (API 35)**

## Wymagania systemowe:

- Co najmniej 80MB wolnej przestrzeni w pamięci urządzenia
- Jedna z wersji Android wymienionych w sekcji ["Kompatybilność"](#kompatybilność)
- Co najmniej 3GB pamięci RAM

(Wymagania przybliżone. Rzeczywiste wymagania mogą się różnić w zależności od wersji)

## Wymagane uprawnienia:

Aplikacja korzysta z następujących uprawnień Android:

- Wysyłanie, usuwanie i modyfikacja powiadomień lokalnych (POST_NOTIFICATIONS) w obrębie pakietu - umożliwia wysyłanie, usuwanie i modyfikację powiadomień na życzenie użytkownika w celu przypomnienia o zbliżających się zadanich. Operacje te potwierdza użytkownik.

- Zarządzanie pamięcią zewnętrzną (MANAGE_EXTERNAL_STORAGE oraz READ_EXTERNAL_STORAGE) - umożliwia wykonanie eksportu i importu danych użytkownika na urządzeniu lokalnym.

## Wykorzystane pakiety NuGet:

- Plugin.LocalNotification:

   Wersja: 12.0.0
   
   Autor: Elvin (Tharindu) Thudugala
   
   Licencja: MIT
   [Link do licencji MIT](https://opensource.org/licenses/MIT)

   [Strona Projektu na GitHub](https://github.com/thudugala/Plugin.LocalNotification)

## Licencja

>Projekt jest objęty licencją "All Rights Reserved". Oznacza to, że wszystkie prawa do tego oprogramowania są zastrzeżone. Kopiowanie, modyfikowanie, rozpowszechnianie, sprzedaż lub jakiekolwiek inne wykorzystanie tego oprogramowania wymaga wyraźnej zgody właściciela praw autorskich.
Na podstawie tej licencji użytkownicy mogą korzystać z tej aplikacji w celach osobistych, ale nie mogą jej modyfikować ani udostępniać bez zgody autora.

## Plan rozwoju:

W ramach projektu przewidziano realizację następujących celów:

1. Dodanie widoku kalendarza
2. Wprowadzenie funkcji archiwizacji zadań
3. Rozbudowa funkcji powiadomień
4. System filtrowania, sortowania oraz flagowania zadań
5. Synchronizacja z chmurą oraz kontem użytkownika
6. Dostęp do zapisanych zadań przez witrynę WWW
7. Dodanie szyfrowania danych użytkownika

---

© 2025 Jakub Kowalik | Wszelkie prawa zastrzeżone.
