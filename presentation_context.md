# Plan Prezentacji: GitHub Copilot dla Angular Developerów (Deep Dive 2026)

## 1. Wstęp: Programowanie AI-Native w 2026
* **Nowy standard:** Przejście od pisania kodu "z palca" do dyrygowania modelami (AI Orchestration).
* **Angular i przewidywalność:** Jak rygorystyczna struktura frameworka (pliki `.ts`, `.html`, `.css`, `.spec.ts`) ułatwia Copilotowi zrozumienie intencji programisty.
* **Weryfikacja:** [GitHub Blog: Copilot Modes & AI Evolution](https://github.blog/ai-and-ml/github-copilot/copilot-ask-edit-and-agent-modes-what-they-do-and-when-to-use-them/)

---

## 2. Nowe Tryby Pracy: Ask, Edit oraz Agent
* **Ask (Chat):** Szybkie konsultacje ("Wyjaśnij mi ten operator RxJS", "Jak zoptymalizować ten Change Detection?").
* **Edit (Inline Edit):** Modyfikacja kodu bezpośrednio w pliku (`Ctrl+I`) – np. dodanie walidacji do istniejącego formularza.
* **Agent Mode:** Copilot jako samodzielny wykonawca – potrafi zaplanować zmiany, stworzyć nowe pliki i zaktualizować importy w całym projekcie (np. przy tworzeniu nowego modułu funkcjonalnego).
* **Weryfikacja:** [GitHub Blog: Ask, Edit, and Agent Modes](https://github.blog/ai-and-ml/github-copilot/copilot-ask-edit-and-agent-modes-what-they-do-and-when-to-use-them/)

---

## 3. Eksperci Domenowi: Uczestnicy Czatu (@)
Nie pytaj "wszystkich", pytaj specjalistów:
* **@workspace:** Posiada pełną wiedzę o strukturze projektu – od `angular.json` po najgłębiej ukryte serwisy.
* **@vscode:** Specjalista od środowiska – pomoże skonfigurować edytor, zainstalować pluginy lub znaleźć błędy w ustawieniach.
* **@terminal:** Tworzenie i naprawianie komend CLI (np. "Wygeneruj komendę `ng generate` dla komponentu z OnPush w konkretnym folderze").
* **Weryfikacja:** [VS Code Docs: Chat Participants](https://code.visualstudio.com/docs/copilot/chat#_chat-participants)

---

## 4. Precyzyjny Kontekst: Zmienne Czatu (#)
Służą do wskazania modelowi, na czym ma się skupić:
* **#selection:** Analizuj tylko to, co zaznaczyłem (idealne do refaktoryzacji długich metod).
* **#file:** Wskaż konkretny plik (np. "Stwórz test na podstawie #file:user.service.ts").
* **#editor:** Kontekst tego, co aktualnie widzisz na ekranie.
* **#codebase:** Przeszukaj cały projekt w poszukiwaniu podobnych wzorców.
* **#git:** Dodaje kontekst aktualnego brancha i historii zmian.
* **#terminalSelection:** Przekaż treść błędu z terminala, aby uzyskać natychmiastową poprawkę.
* **Weryfikacja:** [VS Code Docs: Chat Variables](https://code.visualstudio.com/docs/copilot/chat#_chat-variables)

---

## 5. Angular 2026: Signals, inject() i Standalone
* **Migracja do Signals:** Jak użyć Copilota do bezpiecznej zamiany `BehaviorSubject` na `Signal`.
* **Nowoczesne DI:** Wykorzystanie funkcji `inject()` zamiast konstruktorów – automatyczne czyszczenie kodu.
* **Standalone Components:** Generowanie nowoczesnych komponentów bez zbędnych `NgModule`.
* **Weryfikacja:** [VS Code: Copilot Best Practices](https://code.visualstudio.com/docs/copilot/best-practices)

---

## 6. Automatyzacja Testów Jednostkowych
* **Instant TestBed:** Generowanie pełnych plików `.spec.ts` z poprawną konfiguracją modułów testowych.
* **Mockowanie w locie:** Copilot potrafi stworzyć mocki dla skomplikowanych serwisów na podstawie ich definicji.
* **Edge Cases:** Prośba o wygenerowanie testów dla brzegowych przypadków (np. pusta lista, błąd 500 z API).
* **Weryfikacja:** [GitHub Docs: Copilot Code Completion](https://docs.github.com/en/copilot/responsible-use/copilot-code-completion)

---

## 7. Techniki Promptingu: Podstawy i Struktura
* **Role Prompting:** "Jesteś Senior Angular Developerem, ekspertem od RxJS i wydajności".
* **Delimiters (Ograniczniki):** Używanie `###` lub tagów XML (`<context>...</context>`) do wyraźnego oddzielenia kodu od Twoich instrukcji.
* **Kontekst sąsiednich kart:** Dlaczego warto mieć otwarty plik HTML i TS jednocześnie?

---

## 8. Zaawansowany Prompting: Logika i Rozumowanie
* **Few-Shot Prompting:** Podanie wzorcowego komponentu jako przykładu przed generowaniem kolejnych (wymuszenie spójności stylu).
* **Step-Back Prompting:** "Najpierw opisz strategię zarządzania stanem dla tego modułu, a potem napisz kod".
* **Least-to-Most:** Rozbijanie złożonych zadań (np. integracja z Stripe) na małe kroki logiczne.

---

## 9. Autokorekta i Jakość: Tree of Thought & CoVe
* **Tree of Thought:** Polecenie modelowi wygenerowania 3 różnych podejść (np. `NGRX` vs `Component Store` vs `Signals`) i uzasadnienie wyboru.
* **Self-Refine:** "Sprawdź ten kod pod kątem wycieków pamięci w RxJS i zaproponuj poprawioną wersję".
* **Chain of Verification (CoVe):** "Wygeneruj odpowiedź, a następnie stwórz listę kontrolną, by sprawdzić, czy użyte metody Angulara są zgodne z wersją 19+".

---

## 10. Personalizacja: Custom Instructions
* **Plik `.github/copilot-instructions.md`:** Twój "Style Guide" wczytywany automatycznie do każdego zapytania.
* **Przykłady zasad:** "Zawsze używaj Tailwind CSS", "Stosuj tylko OnPush", "Testy pisz w formacie Gherkin".
* **Weryfikacja:** [GitHub Docs: Custom Instructions Support](https://docs.github.com/en/copilot/reference/custom-instructions-support)

---

## 11. Rozszerzalność: Model Context Protocol (MCP)
* **Wiedza korporacyjna:** Jak połączyć Copilota z wewnętrznym Storybookiem, dokumentacją w Confluence czy specyfikacją API w Swaggerze.
* **Context Bridge:** Dynamiczne dostarczanie wiedzy, której model nie miał w trakcie treningu (np. Twoje wewnętrzne biblioteki UI).
* **Weryfikacja:** [GitHub Docs: Extend Copilot with MCP](https://docs.github.com/en/copilot/how-tos/provide-context/use-mcp/extend-copilot-chat-with-mcp)

---

## 12. Model Comparison: Claude vs GPT
Wybierz silnik do zadania:
* **Claude 3.5 Sonnet:** Bezkonkurencyjny w refaktoryzacji, pisaniu złożonej logiki biznesowej i testów (lepsze rozumowanie).
* **GPT-4o / 4o mini:** Świetny do szybkich pytań, dokumentacji i prostego boilerplate'u.
* **Weryfikacja:** [GitHub Docs: AI Models Comparison](https://docs.github.com/en/copilot/reference/ai-models/model-comparison)

---

## 13. Debugging i Hallucination Patrol
* **Analiza błędów:** Wykorzystanie `#terminalSelection` do zrozumienia błędów kompilacji Angulara.
* **Zwalczanie halucynacji:** Jak weryfikować, czy model nie zmyślił dekoratora lub operatora RxJS (CoVe).
* **Naprawianie selektywne:** Zaznacz błąd w edytorze i użyj `/fix`, aby uzyskać propozycję naprawy.
* **Weryfikacja:** [GitHub Docs: Responsible Use](https://docs.github.com/en/copilot/responsible-use/copilot-code-completion)

---

## 14. Dokumentacja i Clean Code jako Standard
* **Automatyczne JSDoc:** Generowanie opisów metod i parametrów zgodnych ze standardem Twojego zespołu.
* **Generowanie README:** Tworzenie instrukcji obsługi dla nowo stworzonych komponentów / bibliotek.
* **AI Code Review:** Prośba do Copilota o ocenę kodu pod kątem czytelności i zasad Clean Code przed wysłaniem Pull Requesta.

---

## 15. Bezpieczeństwo i Prywatność (Enterprise)
* **Filtrowanie kodu:** Jak Copilot zapobiega kopiowaniu kodu Open Source objętego licencją.
* **Prywatność danych:** Twoje dane nie są wykorzystywane do trenowania modeli publicznych (wersja Business/Enterprise).
* **Zgodność z polityką firmy:** Wykorzystanie audytów logów i kontroli dostępu.