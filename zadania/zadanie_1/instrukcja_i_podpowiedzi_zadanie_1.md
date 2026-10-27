# Zadanie 1: Reflected XSS

W tym zadaniu masz do czynienia z prostą wyszukiwarką. Twoim celem jest wywołanie okienka alert w przeglądarce przy użyciu funkcji `alert(1)`.

## 🎯 Instrukcja
1. Otwórz plik `index.html` z tego folderu w swojej przeglądarce.
2. Spróbuj czegoś wyszukać, np. słowa `test`.
3. Zwróć uwagę na to, co dzieje się z paskiem adresu URL i jak aplikacja wyświetla Twoje zapytanie.
4. Spróbuj wstrzyknąć kod HTML/JS w miejsce wyszukiwanej frazy.

---

### 💡 Podpowiedź 1
<details>
  <summary>Kliknij, aby rozwinąć podpowiedź</summary>
  
  Zauważ, że cokolwiek wpiszesz w pasku wyszukiwania, ląduje w adresie URL jako `?q=TWOJE_ZAPYTANIE`. Spróbuj wpisać tam tagi HTML, np. `<b>test</b>`. Czy tekst pogrubił się na stronie?
</details>

### 💡 Podpowiedź 2
<details>
  <summary>Kliknij, aby rozwinąć podpowiedź</summary>
  
  Skoro strona renderuje tagi HTML, spróbuj użyć tagu `<script>`. Uwaga: w niektórych nowoczesnych przeglądarkach wstrzyknięty tag `<script>` przez `innerHTML` może się nie wykonać bezpośrednio. Wtedy użyj tagu obrazka z błędem!
</details>

### 🚨 ROZWIĄZANIE
<details>
  <summary>Kliknij, aby zobaczyć gotowe rozwiązania</summary>
  
  Wpisz w polu wyszukiwania (lub bezpośrednio w adresie URL po `?q=`) jeden z poniższych payloadów:

  **Opcja 1 (klasyczna):**
  `<script>alert('XSS')</script>`

  **Opcja 2 (omijająca blokady wykonania script przy innerHTML):**
  `<img src=x onerror="alert(document.cookie)">`
</details>