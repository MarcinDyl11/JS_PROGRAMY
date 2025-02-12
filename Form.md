

## 1. Wprowadzenie

Formularze HTML służą do zbierania danych od użytkowników. Dane te mogą być następnie przesyłane do serwera lub odczytywane i przetwarzane lokalnie przez JavaScript. W tej lekcji poznasz:
- Podstawy tworzenia formularza w HTML
- Sposoby definiowania pól formularza (np. pola tekstowe, email)
- Jak odczytać wartości wpisane przez użytkownika przy pomocy JavaScript
- Jak dynamicznie wyświetlić odczytane dane na stronie

Materiały te bazują na przykładach i dokumentacji dostępnej na www.w3school.pl  
cite287

---

## 2. Formularze w HTML – Podstawy

### 2.1. Struktura formularza

Formularz tworzony jest za pomocą znacznika `<form>`, który zawiera różne elementy wejściowe (ang. *input*). Podstawowe elementy to:
- **`<input type="text">`** – pojedyncza linia tekstu (np. imię, nazwisko)
- **`<input type="email">`** – pole na adres email
- **`<button>` lub `<input type="button">`** – przycisk wywołujący akcję (np. odczyt danych)
- **`<label>`** – etykieta opisująca pole, co poprawia dostępność formularza

Przykład prostego formularza:
  
```html
<form id="myForm">
  <label for="imie">Imię:</label>
  <input type="text" id="imie" name="imie" placeholder="Wpisz swoje imię"><br>
  
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" placeholder="Wpisz swój email"><br>
  
  <button type="button" onclick="odczytajDane()">Wyświetl dane</button>
</form>
```

W powyższym przykładzie:
- Każdemu polu przypisano atrybuty **id** oraz **name** – umożliwiają one łatwy dostęp do wartości danego pola (np. za pomocą `document.getElementById`).
- Przycisk typu `button` z atrybutem `onclick` wywołuje funkcję JavaScript, która pobiera dane z formularza.  
cite287

---

## 3. Odczyt danych formularza za pomocą JavaScript

JavaScript umożliwia pobranie wartości wpisanych przez użytkownika. Kluczowym elementem jest metoda `document.getElementById("id_elementu").value`, która zwraca aktualną zawartość pola.

### 3.1. Przykład – Pobieranie i wyświetlanie danych

Poniżej znajduje się kompletny przykład strony, która pobiera dane z formularza i wyświetla je w elemencie `<div>`:

```html
<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8">
  <title>Formularz – Odczyt danych z JavaScript</title>
</head>
<body>
  <h2>Przykładowy formularz</h2>
  
  <form id="myForm">
    <label for="imie">Imię:</label>
    <input type="text" id="imie" name="imie" placeholder="Wpisz swoje imię"><br><br>
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" placeholder="Wpisz swój email"><br><br>
    
    <button type="button" onclick="odczytajDane()">Wyświetl dane</button>
  </form>
  
  <div id="wynik" style="margin-top:20px; padding:10px; border:1px solid #ccc;"></div>
  
  <script>
    function odczytajDane() {
      // Pobranie wartości wpisanych w pola formularza
      var imie = document.getElementById("imie").value;
      var email = document.getElementById("email").value;
      
      // Wyświetlenie danych w elemencie <div> o id "wynik"
      var wynikDiv = document.getElementById("wynik");
      wynikDiv.innerHTML = "<h3>Wprowadzone dane:</h3>" +
                           "<p>Imię: " + imie + "</p>" +
                           "<p>Email: " + email + "</p>";
    }
  </script>
</body>
</html>
```

**Wyjaśnienie przykładu:**
- Sekcja `<form>` zawiera dwa pola: jedno na imię i jedno na email.
- Przycisk „Wyświetl dane” wywołuje funkcję `odczytajDane()`.
- Funkcja `odczytajDane()` pobiera zawartość pól przy użyciu `document.getElementById("...").value` i modyfikuje zawartość elementu `<div id="wynik">`, wyświetlając w ten sposób wprowadzone dane.
  
cite320

---

## 4. Zadania do samodzielnego wykonania

Aby utrwalić zdobytą wiedzę, wykonaj poniższe zadania:

### Zadanie 1: Rozszerz formularz  
Zmodyfikuj powyższy formularz, dodając dodatkowe pola, np. **Nazwisko** oraz **Telefon**. Następnie zmodyfikuj funkcję JavaScript, aby odczytywała również te dane i wyświetlała je w elemencie `<div>`.

*Wskazówki:*
- Dodaj pola `<input type="text">` z odpowiednimi atrybutami `id` i `name`.
- Uzupełnij funkcję `odczytajDane()` o pobieranie nowych wartości i wyświetlanie ich.

### Zadanie 2: Obsługa zdarzenia submit  
Zamiast używać przycisku z atrybutem `onclick`, zmodyfikuj formularz tak, aby przy próbie wysłania formularza (zdarzenie `submit`) wykonywana była funkcja JavaScript. Pamiętaj, aby zapobiec domyślnej akcji przeglądarki (przeładowaniu strony).

*Wskazówki:*
- Użyj atrybutu `onsubmit` w znaczniku `<form>`.
- W funkcji wywoływanej przy submit, użyj `event.preventDefault()`.

### Zadanie 3: Prosta walidacja danych  
Dodaj do funkcji JavaScript walidację – sprawdź, czy pole „Imię” nie jest puste. Jeśli jest puste, wyświetl komunikat (np. za pomocą `alert`) i nie wyświetlaj danych.

*Wskazówki:*
- W funkcji `odczytajDane()`, przed przetwarzaniem danych, sprawdź wartość pola.
- Jeśli wartość jest pusta, wywołaj `alert("Pole Imię nie może być puste!")` i zakończ funkcję (np. `return;`).

---

## 5. Podsumowanie

W tej lekcji poznaliśmy:
- Jak tworzyć formularze w HTML z wykorzystaniem znaczników `<form>`, `<input>` i `<label>`
- Jak odczytywać dane wpisane przez użytkownika przy pomocy JavaScript
- Jak wyświetlać odczytane dane na stronie, modyfikując zawartość elementu HTML
- Przykłady praktyczne oraz zadania do samodzielnej pracy, które pomogą utrwalić zdobyte umiejętności

Dalsze informacje i dodatkowe przykłady znajdziesz na stronie www.w3school.pl, gdzie możesz również eksperymentować z kodem w interaktywnym edytorze.  
cite287  cite320

