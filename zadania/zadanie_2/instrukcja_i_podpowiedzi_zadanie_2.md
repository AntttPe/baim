# Zadanie 2: DOM-based XSS

Tym razem atakowany fragment kodu znajduje się całkowicie po stronie przeglądarki (w pliku JavaScript). Aplikacja wita użytkownika na podstawie tzw. "hasha" z adresu URL.

Twój cel: Ponownie wykonaj kod JavaScript, np. `alert(1)`.

## 🎯 Instrukcja
1. Otwórz plik `index.html` z tego folderu w przeglądarce.
2. Na początku zobaczysz komunikat proszący o dodanie `#TwojeImie` w URL.
3. Zmień adres w przeglądarce dodając na końcu np. `#Jan`, a następnie odśwież stronę (lub wciśnij Enter na pasku adresu).
4. Przeanalizuj kod źródłowy strony i znajdź tzw. *Source* i *Sink* (zgodnie ze slajdem 8).
5. Wykorzystaj to do przemycenia payloadu.

---

### 💡 Podpowiedź 1
<details>
  <summary>Kliknij, aby rozwinąć podpowiedź</summary>
  
  Zajrzyj w kod źródłowy strony (Ctrl+U / Cmd+U). Zobaczysz, że aplikacja używa `location.hash` (to, co występuje po znaku `#` w URL) i wstawia to do strony używając niebezpiecznego `innerHTML`.
</details>

### 💡 Podpowiedź 2
<details>
  <summary>Kliknij, aby rozwinąć podpowiedź</summary>
  
  Co się stanie, jeśli zamiast imienia, po znaku `#` podasz złośliwy kod HTML? Spróbuj wpisać: `#<h1>Test</h1>`.
</details>

### 🚨 ROZWIĄZANIE
<details>
  <summary>Kliknij, aby zobaczyć gotowe rozwiązania</summary>
  
  Zmień adres URL w przeglądarce tak, aby na końcu znalazł się payload XSS, np.:
  `index.html#<img src=x onerror=alert(1)>`

  **Uwaga na temat DOM XSS:** Zauważ, że payload znajdujący się po znaku `#` zazwyczaj w ogóle nie jest wysyłany do serwera. Atak odbywa się wyłącznie w przeglądarce (frontendzie)!
</details>