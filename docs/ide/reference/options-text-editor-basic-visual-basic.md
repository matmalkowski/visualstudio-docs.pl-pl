---
title: Opcje, Edytor tekstów, Basic (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89b73138617583b621b33b31525e3b2f9c89e9e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-basic-visual-basic"></a>Opcje, edytor tekstów, Basic (Visual Basic)
**VB określonych** strony właściwości, **podstawowe** folderu **Edytor tekstu** folderu **opcje** (**narzędzia** menu) — okno dialogowe zawiera następujące właściwości:  
  
 **Automatyczne wstawianie konstrukcji końcowych**  
 Podczas wpisywania — na przykład pierwszy wiersz deklaracji procedury `Sub Main—`i naciśnij klawisz ENTER, Edytor tekstu dodaje odpowiadającego mu `End Sub` wiersza. Podobnie jeśli dodasz [dla](/dotnet/visual-basic/language-reference/statements/for-next-statement) dodaje pętli, Edytor tekstu pasującego `Next` instrukcji. Gdy ta opcja jest zaznaczona, edytora kodu automatycznie dodaje konstrukcji końcowych.  
  
 **Lista pretty (ponowne formatowanie) kodu**  
 Edytor tekstu formatuje kodu zależnie od potrzeb. Gdy ta opcja jest zaznaczona, będzie edytora kodu:  
  
-   Dopasuj kod do położenia odpowiedniej karcie  
  
-   Recase słów kluczowych, zmienne i obiekty do odpowiedniej wielkości liter  
  
-   Dodaj brakujące `Then` do `If...Then` — instrukcja  
  
-   Dodaj nawiasy w celu wywołania funkcji  
  
-   Dodaj brakujące cudzysłowy zakończenia na ciągi  
  
-   Sformatuj ponownie zapis wykładniczy  
  
-   Ponowne formatowanie dat  
  
**Włącz tryb zwijania**  
Po otwarciu pliku w edytorze kodu można wyświetlić w trybu zwijania dokumentu. Zobacz [Tworzenie konspektu](../../ide/outlining.md) Aby uzyskać więcej informacji. Gdy ta opcja jest zaznaczona, funkcja zwijania jest uaktywniany podczas otwierania pliku.  
  
**Automatyczne wstawianie elementów członkowskich Interface i MustOverride**  
Po zatwierdzeniu `Implements` instrukcji lub `Inherits` instrukcji dla klasy, Edytor tekstu wstawia prototypy elementów członkowskich, które mają być implementowane lub została zastąpiona, odpowiednio.  
  
**Pokaż separatory wierszy procedury**  
Edytor tekstu wskazuje zakres visual procedur. Wiersz jest rysowana w plikach źródłowych .vb projektu w lokalizacjach wymienione w poniższej tabeli:  
  
|Lokalizacja w pliku źródłowym .vb|Przykład lokalizację wiersza|  
|---------------------------------|------------------------------|  
|Po zamknięciu konstrukcję deklaracji bloku|-Na końcu klasy, struktury, modułu, interfejsem lub wyliczenia<br />— Po właściwości, function lub sub<br />-Nie między get i set klauzule we właściwości|  
|Po zestaw konstrukcji w jednym wierszu|— Po instrukcje importu, przed definicją typu w pliku klasy<br />— Po zmienne zadeklarowana w klasie przed procedury|  
|Po jednym wierszu deklaracje (z systemem innym niż blok poziomu deklaracje)|-Następujące instrukcje importu, dziedziczy instrukcje, deklaracji zmiennych, deklaracje zdarzeń, delegat, deklaracje i biblioteki DLL zadeklarować — instrukcje|  
  
**Włącz sugestie korekcja błędów**  
Edytor tekstu można sugeruje rozwiązania typowych błędów i umożliwia wybranie odpowiedniego poprawkę, która następnie jest stosowana do kodu.  
  
**Włącz wyróżnianie odwołań i słów kluczowych**  
Edytor tekstu można wyróżnić wszystkich wystąpień symbolu lub wszystkich słów kluczowych w klauzuli takich jak `If..Then`, `While...End While`, lub `Try...Catch...Finally`. Można przechodzić między wyróżnione odwołania lub słowa kluczowe, naciskając klawisze CTRL + SHIFT + Strzałka w dół, strzałki lub CTRL + SHIFT + Strzałka w górę, strzałki.  
  
## <a name="see-also"></a>Zobacz też  
[Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)   
[Opcje, Edytor tekstu, wszystkie języki, karty](../../ide/reference/options-text-editor-all-languages-tabs.md)