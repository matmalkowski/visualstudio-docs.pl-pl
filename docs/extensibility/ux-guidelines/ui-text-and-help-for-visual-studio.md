---
title: Tekst interfejsu użytkownika i pomocy programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 697c794d17f3004b0f37e668ff67afb703490e18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ui-text-and-help-for-visual-studio"></a>Tekst interfejsu użytkownika i pomocy programu Visual Studio
##  <a name="BKMK_UITextAndTerminology"></a> Tekst interfejsu użytkownika i terminologia  
 Tekst zrozumiałymi odgrywa kluczową rolę do wprowadzenia interfejsu użytkownika. Oprogramowanie użytkownicy często odczytać etykiet najpierw, a mianowicie te najodpowiedniejsze do ukończenia zadania. Tekst statyczny jest do odczytu z mniejszą częstotliwością. Plan użytkownikom ich sesje pracy ze całe okno i odczytywanie interfejsu użytkownika w tej kolejności przybliżonej szybkiego skanowania:  
  
1.  Interaktywnych kontrolek w Centrum  
  
2.  Zatwierdź przycisków  
  
3.  Interaktywne kontrolki w innym miejscu  
  
4.  Instrukcje głównego  
  
5.  Dodatkowe objaśnienia  
  
6.  Tytuł okna  
  
7.  Inny statyczny tekst w treści głównej  
  
### <a name="usage-patterns-for-ui-text"></a>Wzorce użycia tekstu interfejsu użytkownika  
  
#### <a name="title-bar-text"></a>Tekst paska tytułu  
 Tekst paska tytułu musi odpowiadać polecenie zduplikowany interfejsu użytkownika.  
  
#### <a name="instructional-text-helper-text"></a>Tekst informacyjny (tekst pomocy)  
 W niektórych oknach dialogowych warto zawierają wyraźne głównego instrukcje wyjaśniają, co należy zrobić w oknie lub na stronie. Jest to czasami określane jako "pomocnika text".  
  
##### <a name="writing-style-rules-for-helper-text"></a>Zapisywanie reguły stylu dla tekstu w pomocy  
  
-   Nie objaśniono oczywiste. Jeśli nie jest bezwzględnie konieczne, nie dołączaj tekst informacyjny.  
  
-   Tekst informacyjny zawsze znajduje się w górnej części okna dialogowego i powinien odwoływać się do zadania wykonywane.  
  
-   Dokładnie Wyjaśnij użytkownikom, muszą zrobić. Unikaj nadmiernego komunikacji i nadmiarowość.  
  
-   Przejrzyj każde okno i eliminowania duplikatów słów i instrukcje.  
  
-   Zachowaj tekst informacyjny krótki. Jeśli więcej informacji jest wymagane dla niektórych użytkowników lub scenariuszy, należy podać link do szczegółowe koncepcyjny temat online.  
  
-   Wpisz tekst, tak aby każdego wyrazu zawiera wagi i jest konieczne.  
  
-   Postępuj zgodnie z istniejącą firmy Microsoft dotyczące [tekst interfejsu użytkownika](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) i [styl i ton](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="supplemental-instructions"></a>Dodatkowe instrukcje  
 Dodatkowe instrukcje znajdują się dodatkowe informacje, które ułatwia użytkownikom zrozumienie kontrolki lub kontroli grupowania. Może to być również konieczne do zrozumienia format oczekuje kontrolki wprowadzania tekstu podpowiedzi. Użyj instrukcji uzupełniające oszczędnie. Zarezerwować je dla przypadków, kiedy istnieje prawdopodobieństwo, że użytkownik nie będzie lepiej zrozumieć konsekwencje wybór one dokonywania.  
  
 ![Uzupełniające tekstu w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Uzupełniające tekstu w programie Visual Studio**  
  
 ![Uzupełniające tekstu w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Uzupełniające tekstu w programie Visual Studio**  
  
#### <a name="infotips"></a>InfoTips  
 Często tekst informacyjny może być zbyt obszerne, aby umieścić w miejscu w interfejsie użytkownika lub może być przydatna dla nowych użytkowników Cierpisz jak bałaganu do doświadczeni użytkownicy. W takim przypadku należy umieścić tekst informacyjny/informacyjny jako etykietka narzędzia w obszarze poradę.  
  
 InfoTips powinna zostać umieszczona w pobliżu formanty są związane z a należy użyć określonej ikony Porada jest jeszcze dyskretny kod zauważalne.  
  
 ![Porada w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Przykładem porady w programie Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Zapisywanie reguły stylu InfoTips  
  
-   Zapis InfoTips jako pełnych zdań. Wymagają one określonych zleceń, zdaniu i kończenie znaków interpunkcyjnych.  
  
-   Użyj InfoTips uzupełnienie informacje lub głównej instrukcji. Jeśli używane są tylko innych wyrazów przekształcenie danych główny pomysł, nie potrzebujesz poradę.  
  
-   Zachowaj InfoTips krótkich słodkich. Użyj słowa małe i zwykłego, codzienne języka, który obsługuje i zachęca użytkownika.  
  
-   Postępuj zgodnie z istniejącą firmy Microsoft dotyczące [tekst interfejsu użytkownika](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) i [styl i ton](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="control-labels"></a>Etykiety formantu  
 Etykiety formantu powinna być krótka i zwięzłe i wykonaj [pulpitu systemu Windows dotyczące kontroli](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Aby uzyskać więcej informacji na temat format etykiety formantu i umieszczanie w Interfejsie użytkownika dotyczą [układu dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Łącza pomocy  
 Łącza pomocy albo można umieścić tekst informacyjny lub w treści interfejsu użytkownika. Mogą zostać łącza pomocy albo uruchom wewnętrzny okien dialogowych.  
  
##### <a name="visual-style-rules-for-help-links"></a>Reguły stylu dla łącza pomocy  
  
-   Użyj kolorów poprawne środowisko dla hiperłącza. Poprawnie styl hiperłączy nie zostaną krótko flash czerwony po kliknięciu. Jeśli widzisz taki komunikat, to wskazanie, że środowisko kolorów nie są używane.  
  
-   Podkreślenie powinien być używany tylko w przesuwania lub gdy łącze jest osadzony w akapitu.  
  
-   Aby uzyskać szczegółowe informacje, style wizualne i interakcji hiperłącza Zobacz przycisków i hiperłącza.  
  
##### <a name="writing-style-rules-for-help-links"></a>Zapisywanie reguły stylu dla łącza pomocy  
  
-   Podczas uruchamiania okien dialogowych, obsługa normami wielokropek: nie wielokropka nawigacji, wielokropek, jeśli zadanie wymaga dodatkowych interfejsu użytkownika.  
  
     ![Link pomoc w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 e_HelpLink")  
  
     **Wielokropek (...) łącza pomocy wskazuje, że zadanie będzie wymagać dodatkowego interfejsu użytkownika.**  
  
-   Łącza nie powinny rozpoczynać "Dowiedz się więcej", ponieważ nie jest celem użytkownika. Użytkownik chce odpowiedzi na konkretne pytanie, nie będą otrzymywali edukacji ogólne.  
  
-   Pomoc frazy łączy tak, aby ich zadać sobie pytanie odpowie tematu.  
  
     Niepoprawne:  
     "Dowiedz się więcej o cenach systemu Windows Azure Mobile Services"  
  
     Popraw:  
     "Jakie cenowej są dostępne opcje dla usług mobilnych Microsoft Azure?"  
  
-   Nigdy nie używaj *kliknij...*  tekst łącza.  
  
-   Nigdy nie łącze tylko słowa "tutaj". Jest to powodować problemy dla niektórych czytników ekranu, które będą głosowych Link słowo.  
  
     Niepoprawne:  
     "Informacje dotyczące usług mobilnych Microsoft Azure **tutaj**"  
  
     Popraw:  
     "Jakie cenowej są dostępne opcje dla usług mobilnych Microsoft Azure?"  
  
-   Aby uzyskać więcej informacji o stylu pisania poprawne dla łącza pomocy, zobacz [wskazówki pulpitu systemu Windows, aby uzyskać Pomoc](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### <a name="hint-text"></a>Tekst wskazówki  
 Wskazówka tekst jest wyświetlany jako znak wodny w formancie lub poniżej formantu. Poprawnego formatowania zostaną zastosowane przy użyciu odpowiedniego tokenu VSColors, `Environment.GrayText`.  
  
 Może być wyświetlany w wielu formularzach.  
  
-   Zamiast etykiety kontroli:  
  
     ![Wskazówki tekstu w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 f_HintText1")  
  
-   Ze zleceniem ze wskazówkami:  
  
     ![Wskazówki tekstu w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 g_HintText2")  
  
-   Tekst zawierający wymaganego wpisu:  
  
     ![Wskazówki tekstu w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>Tekstu znaku wodnego  
 Na powierzchni projektu pusty tekst powinny wskazywać, co należy zrobić, a także łącza, aby otworzyć inne pokrewne systemu windows, w razie potrzeby:  
  
 ![Znak wodny tekstu w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 i_WatermarkText")  
  
 **Przykład tekstu znaku wodnego w programie Visual Studio**  
  
### <a name="common-terminology"></a>Wspólna terminologia  
  
|Termin|Wyjaśnienie|Komentarz|  
|----------|-----------------|-------------|  
|Zaloguj się / Wyloguj|Używany jako synonim z sieci web do uwierzytelniania w sieci web właściwość zleceń. W ramach klientów korzystamy z tym razem jako pojęcie najwyższego poziomu do podpisywania i połączenia użytkownika IDE, które reprezentuje tożsamość najwyższego poziomu, który zapewnia możliwości wyższego poziomu, takich jak roaming i licencjonowania, które nie są dostępne w innych połączeń.|Użytkownika IDE jest jedyną funkcją powinny reprezentować logowania / Wyloguj zlecenie, ponieważ reprezentuje on użytkownika IDE najwyższego poziomu.|  
|Połącz / Rozłącz|Użyj w miejscach, w którym funkcja zajmuje pojedynczego połączenia się z usługami online.|Eksploratora serwera, gdzie można mieć tylko jedno aktywne połączenie platformy Azure w czasie, jest przykładem łączenia/rozłączania.|  
|Dodawanie lub usuwanie|Non destrukcyjnie. Opcja używana podczas dodawania lub usuwania elementu z listy.|Okno dialogowe listy serwera TFS Menedżera połączeń jest przykładem Dodaj lub Usuń.|  
|Usuwanie|Destrukcyjnie. Użyj tylko wtedy, gdy element usuwana zostaną trwale odrzucone lub usuwane z dysku.|Zazwyczaj "Delete" wymaga monitu, jeśli wynik usuwa plik z dysku.|  
  
## <a name="error-messages"></a>Komunikaty o błędach  
  
### <a name="overview"></a>Omówienie  
 Wystąpić błędy. Ustawienie ograniczenia na czynności użytkownika jest za pośrednictwem pierwszy krok w celu zapobiegania zbędnego komunikaty. Jednak w przypadku wystąpienia błędu, komunikat o błędzie dobrze napisane można zdecydowanie kierunku zmniejszenia problem. Komunikaty o błędach raczej są jednym z najważniejszych typów powiadomień, który użytkownik widzi, ponieważ są synchroniczne i wskazują na problem, który ma zostać rozwiązane. Niepoprawnie napisane komunikaty pozostaw użytkowników własne podjęcie przyczyna błędów i wszystkie możliwe rozwiązania.  
  
 Użytkownicy mogą zatrzymać, zwracając uwagę nadmiernego obciążenia lub skomplikowana komunikaty o błędach, więc wystąpić wiadomości tylko niezbędne zapisu, które Dodaj wartość do użytkownika. Jeśli komunikat jest po prostu powiadomienia, należy użyć alternatywnych prezentacji.  
  
### <a name="rules-for-creating-an-error-message"></a>Reguły tworzenia komunikat o błędzie  
  
-   Podczas konstruowania komunikaty o błędach, należy wybrać poziom błędu odpowiednie dla odbiorców. Staraj się proste podsumowania, które zapewniają akcji użytkownika może trwać, jeśli ma to zastosowanie. Stan nie wszystko, co użytkownik nie musi wiedzieć.  
  
-   Zapewnianie pomocy zwyczajowo. Jest łatwiej odczytywać i działają na komunikat o błędzie, który zawiera instrukcję.  
  
-   Nie używaj negatywów o podwójnej precyzji.  
  
-   Wykonaj zarówno automatycznego i ręcznego gramatyki i pisowni sprawdzić wszelkie komunikaty o błędach, zostanie zapisany.  
  
-   Złożone komunikatów o błędach należy unikać sekwencyjnych komunikacji. Nigdy nie używaj podłączenie F1 komunikat o błędzie. Wiadomości powinna być wystarczająca.  
  
-   Użyj ikony jest poprawna.  
  
-   Wprowadź pytania łatwe do zrozumienia i użyj przycisków, który ma wyczyść opcje, takie jak "Delete" i "Anuluj".  
  
-   Ostrzeżenia znać jaki będzie konsekwencją postępowania. Przyciski powinny wskazywać, konsekwencją.  
  
-   Błędy opisano, co użytkownik może wykonać, aby rozwiązać ten problem. Przyciski powinna być akcje lub Wypowiedz "Zamknij". Przycisk "OK" nie jest używany do komunikat o błędzie.  
  
-   Niektóre pytania samodzielnie podczas konstruowania komunikat o błędzie:  
  
    -   Czy użytkownika można dowiedzieć się, jak rozwiązać problem z tym błędem wyłącznie?  
  
    -   Użytkownik używa tego samego słownictwa jako ten błąd?  
  
    -   Jest to błąd ambigious lub udostępniać w wielu sytuacjach? Jeśli tak, jak możesz prowadzą użytkowników do rozwiązania, które są im potrzebne?  
  
#### <a name="build-errors"></a>Błędy kompilacji  
 Ponieważ Visual Studio jest narzędziem do rozwoju oprogramowania, wiele składników ma kompilacji, konwertowanie lub kodowania krok, aby przekonwertować pracy dewelopera na format binarny. Konwersje te mogą powodować błędy, gdy kompilator nie może przetworzyć nieprawidłowo utworzone pliki lub opcje kompilatora nie zostały poprawnie skonfigurowane.  
  
 Użytkowników programu Visual Studio może przeznaczyć olbrzymią liczbę godzin programowanie Rozwiązywanie błędów kompilacji. Zwiększa to czas rozwiązania błędów ma zależności lub gdy komunikaty o błędach są nieprawidłowo zapisywane, który może utrudniać do ujawniania źródła błędu.  
  
 Najważniejsze błędy kompilacji są te, które nie występują w pierwszym miejscu, dlatego program Visual Studio udostępnia autouzupełniania i zygzaki funkcji IntelliSense. Moduły weryfikacji schematu i podobne narzędzia zapewniają tego samego rodzaju opinię. Tych mechanizmów prowadzić aktywnego użytkownika do skonstruowania poprawnie sformułowany kod, zmniejszenie ryzyko błędów kompilacji.  
  
 Program Visual Studio udostępnia okna narzędzia, w którym użytkownicy mogą odczytać i nawigowania błędów, które wystąpiły podczas ich okna dokumentów. Skróty klawiaturowe są dostarczane, dzięki czemu użytkownik może szybko przejść dużych ilości kodu i przejść bezpośrednio do lokalizacji problemu. Program Visual Studio umożliwia również każdego błędu kompilacji ograniczeni do określonego Identyfikatora — słowo kluczowe/kontekstu pomocy, dzięki czemu użytkownik może przejść bezpośrednio do tematu pomocy, który zapewnia bardziej szczegółowe informacje o błędzie.  
  
 Błędy kompilacji zrozumiałe i zwięzłe zapisu:  
  
-   **Użyj prostego języka** objaśniający problem z żadnych żargonu kompilatora. Tekst błędu kompilacji nie może być nadmiernie technicznych.  
  
-   **Opisano możliwe przyczyny.** Na przykład "Brak dwukropka pomiędzy właściwością, a wartość" (właściwość): (wartość) "deklaracji."  
  
-   Należy podać szczegóły dotyczące potencjalnego poprawki. Jeśli nie ma wystarczającej ilości miejsca, dodatkowe informacje mogą być wprowadzane do odpowiedniego tematu Pomocy.  
  
### <a name="components-of-a-well-written-error-message"></a>Składniki komunikatu o błędzie dobrze napisane  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Użyj okna dialogowego powłoki komunikaty o błędach.  
 Za pomocą usługi powłoki okna dialogowego pozwala sterować wyglądem komunikatu czcionek w szczególności bez najważniejszych zmian do poszczególnych elementów. Użyj **IErrorInfo** mechanizmów i raportuj je przy użyciu **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Wybierz prezentacji skuteczne i odpowiednie powiadomienie.  
 Za pomocą modalnego okna dialogowego krytyczne Ostrzeżenie Jeśli natychmiastowych akcji jest wymagany w celu uniknięcia utraty danych (synchroniczne powiadomienia). Krytyczne ikony są zarezerwowane do sytuacji, w których zamknięcia wiadomość bez odczytu może to prowadzić do negatywne skutki. Utrata danych jest sytuacji krytycznych, która wymaga odpowiedzi poziom alarmu. Nadmierne zużycie krytyczne ikony desensitizes użytkownikom jego znaczenie. Komunikat o błędzie jest informacyjne, należy wziąć pod uwagę alternatyw modalnego okna dialogowego (asynchroniczne powiadomienia).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Podaj czyste, zwięzły opis przyczynę wystąpienia problemu, a nie technicznej wyjaśnienie.  
 Nadmiernego obciążania użytkownikom szczegółowe informacje techniczne wyjaśnienie spowoduje, że ich bardziej prawdopodobne zignorować komunikaty o błędach. Przykłady dobra do obsługi komunikatów:  
  
-   "Nie można otworzyć żądanego pliku."  
  
-   "Nie można połączyć się z Internetem."  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Zawierają informacje dotyczące sposobu rozwiązania problemu.  
 Oferuj sugestii użytkownika, jak rozwiązać ten problem. Przyznaj się z użytkownikiem w przypadku żadne sugestie. Podaj linki bezpośrednie do alternatywnego online źródeł, takich jak pomoc techniczna lub techniczna dla społeczności. Spróbuj wskaż użytkowników określonych informacji online właściwą problem. Identyfikator błędu należy wziąć pod uwagę łączenie użytkowników z wątku dyskusji dotyczących tego błędu. Przykłady dobra do obsługi komunikatów:  
  
-   "Upewnij się, czy są połączone z Internetem i spróbuj wykonać tę operację ponownie."  
  
-   "Upewnij się, że plik istnieje i czy masz uprawnienia, aby go otworzyć."  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Wpisz komunikat, który jest krótko- i do punktu.  
 Komunikat o błędzie mogą wyświetlać powiadomienia, wyjaśniają i oferuje rozwiązania jednak nadal jest ignorowana, jeśli jest zbyt długi. Rozwiązanie polega na ujawnienie progresywnego za pomocą przycisku Szczegóły. Na przykład podać krótki opis/rozwiązania, a następnie umieść więcej szczegółów w obszarze przycisk Szczegóły. Jeśli użytkownik wybierze uzyskać więcej informacji na temat błędu, ich można to zrobić.  
  
 Język wiadomości powinna być:  
  
-   **Odpowiednie domeny.** Używać języka zostanie zrozumiałą dla użytkownika. Chociaż naszym klientom deweloperów, często nie posiadają kontekstu i terminologii, który mamy.  
  
-   **Określone.** Unikaj niezrozumiała treść i przypisz konkretne nazwy i lokalizacje obiektów związanych. Na przykład komunikat o błędzie, takie jak "znak jest nieprawidłowy" nie jest użyteczne. Znak, który? "Nie można odnaleźć pliku". Plik, który?  
  
-   **Uprzejmy.** Nie blame użytkownika lub wprowadzić je uznać stupid. Unikaj szkodliwy lub obraźliwy język (kill, wykonanie, przerwanie krytyczny, niedozwolony). Unikaj tekstu pisanego wielkimi literami, która jest często postrzegane jako shouting, a nie jako możliwy. Nie używaj humor.  
  
-   **Popraw.** Użyj poprawianie błędów pisowni i gramatyki (nawet w parametrami wymaganymi). Błędów pisowni są szkodzi i Zakłopotanie.  
  
-   **Użycie odpowiednich.** Użyj tekstu odpowiedni przycisk. Unikaj przycisk "OK", a zamiast tego użyj "Continue" lub "Yes/No".  
  
### <a name="error-message-examples"></a>Przykłady komunikat błędu  
  
|Dobra|Zły|  
|----------|---------|  
|"Numer wybierany jest już w usłudze. Sprawdź numer i spróbuj ponownie lub wybierz 0 dla operatora."|-"Błąd (449): niedozwolony numer"<br />-"Ten błąd nieobsługiwany wyjątek wskazuje, że operacja została ukończona pomyślnie."<br /><br /> ![Nieprawidłowy komunikat w programie Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>Uzyskiwanie dostępu do pomocy  
  
### <a name="overview"></a>Omówienie  
 Oprócz dokumentacji w witrynie MSDN użytkownika programu Visual Studio ma kilka punktów dostępu do pomocy użytkownika znajduje się w interfejsie użytkownika. Aby upewnić się, że te punkty dostępu są stale dostępne, zespołów funkcji należy skorzystać z systemu pomocy oferowane przez środowisko. Te punkty dostępu są:  
  
-   **Tekst informacyjny i dodatkowych w oknach dialogowych.** Tekst statyczny określające kierunek lub wyjaśnienie, albo w Interfejsie użytkownika powierzchni lub dostępne w Przesuń kursor myszy ikona porady.  
  
-   **Pomoc F1** (tylko w edytorze). W edytorze programu Visual Studio można ufać użytkownika, że w dowolnym momencie naciśnięcie klawisza F1 powoduje wyświetlenie tematu Pomocy specyficzne dla bieżącego zaznaczenia. Upewnij się, że tematy związane z F1 są odpowiednie i informacji.  
  
-   **Hiperłącza do tematów Pomocy.** Hiperłącze w oknie dialogowym, okna narzędzia lub powierzchni projektowej, uruchamianą tematów pomocy użytkownika dowiedzieć się więcej na temat technologii, funkcji lub informacji o sposobie wykonania zadania.  
  
-   **Mechanizmy interfejsu użytkownika pomocnika, takich jak tagi inteligentne i tworzenie okien dialogowych.** Te mechanizmy ułatwi użytkownika opis elementu interfejsu użytkownika lub ułatwienia zadania, takie jak tagi inteligentne lub konstruktora w oknach dialogowych.  
  
-   **Przyciski pomocy interfejsu użytkownika** (przestarzałe). Wskaźnik widoczna na pasku tytułu, który zapewnia dostęp do powiązanych tematów pomocy F1.  
  
### <a name="text"></a>Tekst  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Tekst informacyjny i dodatkowych w oknach dialogowych  
 W oknach dialogowych, które obsługują złożonych zadań może być trzeba nadać tekstu informacyjnego w Interfejsie użytkownika, często u góry okna dialogowego lub w jego pobliżu złożonych kontrolek. Zobacz [interfejsu użytkownika tekstu i terminologię](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) szczegółowe informacje dotyczące stylu pisania.  
  
#### <a name="infotips"></a>InfoTips  
 Często tekst informacyjny może być zbyt obszerne, aby umieścić w miejscu w interfejsie użytkownika lub może być przydatna dla nowych użytkowników Cierpisz jak bałaganu do doświadczeni użytkownicy. W takim przypadku należy umieścić tekst informacyjny/informacyjny jako etykietka narzędzia w obszarze poradę.  
  
 InfoTips powinna zostać umieszczona w pobliżu formanty są związane z a należy użyć określonej ikony Porada jest jeszcze dyskretny kod zauważalne.  
  
 ![Porada w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Przykładem porady w programie Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Interakcyjne mechanizmów pomocy  
  
#### <a name="f1-help"></a>Pomoc F1  
 Wymagana jest pomocy F1 w edytorze lub powierzchni projektu, ale nie w innym miejscu w środowisku Visual Studio.  
  
#### <a name="hyperlinks-to-help-topics"></a>Hiperłącza do tematów pomocy  
 Hiperłącza może służyć do wykonywania akcji, przejdź w środowisku IDE lub uruchomić pomocy w przeglądarce. Zobacz [interfejsu użytkownika tekstu i terminologię](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) szczegółowe informacje o języku i 07.10.01 przycisków i hiperłączy wskazówki wizualne i układu.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Pomoc [?] przycisków pasków tytułu okna dialogowego (przestarzałe)  
 W większości przypadków przyciski pomocy [?] w pasku tytułu okna dialogowe są przestarzałe. Tematy interfejsu użytkownika nie są już częścią naszego modelu doc, a w związku z tym mogą nie istnieć odpowiedni temat, aby połączyć. Zasadniczo przycisk paska tytułu był samym co pomocy F1, a nie jest wymagany w oknach dialogowych. W niektórych przypadkach to można nadal będzie używana jako wskaźnik dostępne jest więcej informacji o pojęciach i procedurach Chociaż hiperłącza najczęściej używanych w nowszej interfejsu użytkownika.  
  
##### <a name="dialogs-created-through-the-environment"></a>Okna dialogowe został utworzony za pomocą środowiska  
 Wiele okien dialogowych powłoki są tworzone za pomocą **VBDialogBoxParam** funkcji. Ta funkcja udostępnionych zostało zaktualizowane ułatwiają przenoszenie **pomocy** przycisk z okna dialogowego do **?** przycisk przy zachowaniu architekturę wstecz zgodny i rozszerzalny.  
  
 W szczególności **VBDialogBoxParam** funkcja analizuje szablonu okna dialogowego o identyfikatorze przycisku **IDHELP** (9) lub etykieta jest **pomocy** lub **&pomocy**. Jeśli zostanie znaleziony przycisk Pomoc, jest ukryta i **ws_ex_contexthelp —** styl jest dodawany do okna dialogowego, który umieszcza **?** przycisku w pasku tytułu okna dialogowego.  
  
 Podczas tworzenia okna dialogowego wypchnięcia proc okna dialogowego na stosie i wywołuje okno dialogowe z przetwarzania wstępnego proc okna dialogowego o nazwie **DialogPreProc**. Gdy **?** kliknięto przycisk wysyła **WM_SYSCOMMAND** z **SC_CONTEXTHELP** do okna dialogowego. **DialogPreProc** przechwytuje tego polecenia i zmienia jego **WM_HELP** komunikat, który jest przekazywany do oryginalnego obrady okna dialogowego  
  
 Większość okien dialogowych utworzyć środowiska ma przycisk Pomoc w oknie dialogowym. Po wyświetleniu okna dialogowego przycisk Pomoc jest ukrywane automatycznie **?** przycisk działa. Jeśli **?** przycisk kiedykolwiek usunięte lub zmienione w systemie Windows, to rozwiązanie umożliwia szybko powrócić do oryginalnej przyciski pomocy.  
  
 To rozwiązanie powoduje cztery założenia, które mogą powodować błędy:  
  
-   Przycisk Pomoc w oknie dialogowym jest **IDHELP** (9).  
  
-   Okno dialogowe wygląda poprawnie, gdy przycisk Pomoc jest ukryty.  
  
-   Okno dialogowe nie zastępuje jego modułu winproc wartości.  
  
-   Okno dialogowe nie jest osadzony wewnątrz innego okna dialogowego.  
  
 Jeśli Twoje okno dialogowe znajduje się w msenv i nie używa **VBDialogBoxParam**, zbadaj wykorzystaniu **VBDialogBoxParam** przed wdrożeniem własne obsługi.  
  
##### <a name="dialogs-created-through-other-packages"></a>Utworzone przez inne pakiety w oknach dialogowych  
 Można implementować rozwiązania w oknach dialogowych, które znajdują się poza msenv. Dla klasy okien dialogowych udostępnionych w pakiecie VSPackage rozważ przejście przycisk paska tytułu lub Implementowanie obsługi w każdym oknie dialogowym. Następujący kod jest szkielet implementacji, aby pomóc Ci rozpocząć:  
  
```  
struct DLGPROCITEM  
{  
    FARPROC proc; // The info used to create the dialog.  
    DLGPROCITEM* procPrev;  
};  
  
DLGPROCITEM* g_dlgProcStack = NULL;  
  
// A dialog starter/wrapper function is used to push the new  
// dialog proc to the top of our dialog proc stack.  
  
int SomeDialogStarterFunction(hinst, id, proc, etc)  
{  
    if (g_dlgProcStack == NULL)  
    {  
        g_dlgProcStack = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = NULL;  
    }  
    else  
    {  
        DLGPROCITEM* procItem = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = g_dlgProcStack;  
        g_dlgProcStack = procItem;  
    }  
}  
  
// Pop this dialog proc off the dialog proc stack.  
  
DialogBoxIndirectParam...(...)  
{  
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;  
    delete g_dlgProcStack;  
    g_dlgProcStack = procItem;  
}  
  
// A wrapper dialog procedure will allow us to capture the  
// SC_CONTEXTHELP button on the title bar from Windows and  
// forward it as a simple WM_HELP message back to the dialog.  
  
INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,  
    WPARAM wParam, LPARAM lParam)  
{  
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)  
    {  
        uMsg = WM_HELP;  
        wParam = 0;  
        lParam = 0;  
    }  
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,  
        hwndDlg, uMsg, wParam, lParam);  
}  
```  
  
##### <a name="help-buttons-in-managed-code"></a>Przyciski pomocy w kodzie zarządzanym  
 Zastępowanie zachowania domyślnego przycisk Pomoc pasek tytułu okna jest łatwy w kodzie zarządzanym. Poniżej znajdują się aplikacji pokaz pełną, który demonstruje to zachowanie. W zasadzie należy zastąpić formularza **WndProc** — metoda i następnie fire wyłączanie pomocy F1 żądania, gdy **SC_CONTEXTHELP** wiadomość zostanie przechwycona.  
  
```  
using System;  
using System.Windows.Forms;  
  
public class HelpForm : Form  
{  
    private const int SC_CONTEXTHELP = 0xF180;  
    private const int WM_SYSCOMMAND = 0x0112;  
  
    public HelpForm()  
    {  
        this.ClientSize = new System.Drawing.Size(300, 250);  
        this.HelpButton = true;  
        this.MaximizeBox = false;  
        this.MinimizeBox = false;  
        this.Name = "HelpForm";  
        this.Text = "Help Form";  
    }  
  
    protected override void WndProc(ref Message m)  
    {  
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)  
            ShowHelp();  
        else  
            base.WndProc(ref m);  
    }  
  
    private void ShowHelp()  
    {  
        MessageBox.Show("F1 Help goes here.");  
    }  
  
     [STAThread]  
    static void Main()  
    {  
        Application.EnableVisualStyles();  
        Application.EnableRTLMirroring();  
        Application.Run(new HelpForm());  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Czcionki i formatowania dla programu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Układ dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Powiadomienia i postępu dla programu Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)