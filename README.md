## Zadanie 1 (nazwa brancha: zad1)

Utwórz plik `Main.java` w głównym katalogu. Niech spełnia następujące założenia:

### Main.java:

- Dziedziczy po `Application` (z JavaFX).
- Ma prywatną zmienną typu `TextField` o nazwie `directoryPathField`.
- Ma prywatną zmienną typu `TextField` o nazwie `searchField`.
- Przesłania metodę `start`, przyjmującą jako argument `primaryStage` typu `Stage`, oraz:
  - Ustawia tytuł aplikacji na „File Browser and Search”.
  - Przypisuje do `directoryPathField` nową instancję klasy `TextField`.
  - Ustawia placeholder inputa `directoryPathField` na „Enter directory path”.
  - Przypisuje do `searchField` nową instancję klasy `TextField`.
  - Ustawia placeholder inputa `searchField` na „Enter search phrase”.
  - Tworzy zmienną `browseButton` przechowującą instancję klasy `Button` o nazwie „Browse”.
  - Dodaje obsługę zdarzenia do `browseButton`, która wywoła `browseDirectory`.
  - Tworzy zmienną `searchButton` przechowującą instancję klasy `Button` o nazwie „Search”.
  - Tworzy zmienną `hBox` przechowującą instancję klasy `HBox`, zainicjalizowaną parametrami 10, `directoryPathField` oraz `browseButton`.
  - Tworzy zmienną `vBox` przechowującą instancję klasy `VBox`, zainicjalizowaną parametrami 10, `hBox`, `searchField` oraz `searchButton`.
  - Tworzy zmienną `scene` przechowującą instancję klasy `Scene`, zainicjalizowaną parametrami `vBox`, 600 oraz 200.
  - Ustawia `scene` jako scenę `primaryStage`.
  - Wyświetla aplikację za pomocą `primaryStage`.

- Ma prywatną metodę `browseDirectory`, która:
  - Tworzy zmienną `directoryChooser` przechowującą instancję klasy `DirectoryChooser`.
  - Tworzy zmienną `selectedDirectory` przechowującą informację na temat wyświetlenia modalu/dialogu z `directoryChooser` ustawioną na null.
  - Sprawdza czy `selectedDirectory` jest różny od null, a jeżeli tak, ustawia tekst `directoryPathField` na ścieżkę absolutną za pomocą `selectedDirectory`.

- Metoda `main` wyzwala metodę `launch` do której przekazuje `args`.

## Zadanie 2 (nazwa brancha: zad2)

Zaktualizuj plik `Main.java` w następujący sposób:

- Dodaj nową prywatną zmienną typu `TextArea` o nazwie `resultArea`.
- Zaktualizuj metodę `start` by uwzględniała `TextArea` i ustawiała jego preferowaną wysokość na 400.
- Przekaż go do `vBox` jako kolejny parametr.

## Zadanie 3 (nazwa brancha: zad3)

Zaktualizuj plik `Main.java` w następujący sposób:

- Dodaj obsługę zdarzenia dla `searchButton`, która wywoła `searchFiles`.
- Dodaj metodę `searchFiles`, która:
  - W przypadku gdy `directoryPath` jest pusty, ustawi w `resultArea` tekst „Please provide a directory path.”
  - Tworzy zmienną `directory` przechowującą instancję klasy `File` zainicjalizowany parametrem `directoryPath`.
  - W przypadku gdy podana ścieżka nie jest katalogiem, ustawi w `resultArea` tekst „The provided path is not a directory.”
  - Tworzy zmienną `results` przechowującą instancję klasy `StringBuilder`.
  - Wywołuje metodę `searchInDirectory`, która przyjmuje jako argumenty `directory` oraz `results`.
  - Wczytuje listę wyników wyszukiwania i ustawia je w `resultArea` jako tekst.

- Dodaj metodę `searchInDirectory`, która:
  - Zwraca listę wyszukanych plików w wybranym katalogu jako rozszerzenie `results` przekazanego do niej jako argumentu,
  - Każdy zwrócony w ten sposób plik ma być wyświetlony w nowej linii.

## Zadanie 4 (nazwa brancha: zad4)

Zaktualizuj plik `Main.java` w następujący sposób:

- Dodaj metodę `containsPhrase`, która:
  - Zwraca boolean,
  - Przyjmuje jako argumenty `file(File)` oraz `searchPhrase(String)`,
  - Implementuje wyjątek `IOException`.
  - Za pomocą bloku `try … catch`:
    - Sprawdza czy odczytywana linia zawiera szukaną frazę, jeżeli tak to zwraca true,
    - W przypadku błędu zwraca wyjątek.
  - W jakimkolwiek innym przypadku zwraca false.

- Przemień `listFilesInDirectory` na `searchInDirectory` oraz przekaż do niego dodatkowy argument `searchPhrase`.
- Zaktualizuj kod tak, aby wykorzystywał w odpowiednich miejscach `containsPhrase` tak, żeby zwracał jedynie te pliki w wybranym katalogu, które pasują do wyszukiwanej frazy.
