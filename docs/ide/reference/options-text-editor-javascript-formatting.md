---
title: Opcje, edytor tekstu, JavaScript, formatowanie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84c2f89aa578aa8b2c3c9ea4d033a5cff66a238e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950884"
---
# <a name="options-text-editor-javascript-formatting"></a>Opcje, edytor tekstu, JavaScript, formatowanie
Użyj **formatowanie** strony **opcje** okno dialogowe, aby ustawić opcje formatowania kodu w edytorze kodu. Dostępu do tej strony, na pasku menu wybierz **narzędzia**, **opcje**, a następnie rozwiń węzeł **Edytor tekstu**, **JavaScript**i **Formatowania**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Automatyczne formatowanie
 Opcje te określają, kiedy formatowanie występuje w **źródła** widoku.

## <a name="uielement-list"></a>Lista elementów UI

|Opcja|Opis|
|------------|-----------------|
|**Formatuj ukończony wiersz po Enter**|Gdy ta opcja jest zaznaczona, edytora kodu automatycznie formatuje wiersz po wybraniu klawisz Enter.|
|**Formatuj ukończony instrukcji.**|Gdy ta opcja jest zaznaczona, edytora kodu automatycznie formatuje wiersz, w przypadku klucza średnika.|
|**Formatuj ukończony blok na}**|Gdy ta opcja jest zaznaczona, edytora kodu automatycznie formatuje wiersz po wybraniu zamykający nawias klamrowy klucza.|
|**Format po wklejeniu**|Gdy ta opcja jest zaznaczona, edytora kodu formatuje kodu podczas wklejania do edytora. Edytor używa obecnie zdefiniowane reguły formatowania. Jeśli ta opcja nie jest zaznaczona, Edytor używa oryginalne formatowanie kodu wkleić w.|

## <a name="new-lines"></a>Nowe wiersze
 Opcje te określają, czy edytor kodu umieszcza otwierający nawias klamrowy funkcje i bloków kontroli w nowym wierszu.

## <a name="uielement-list"></a>Lista elementów UI

|Opcja|Opis|
|------------|-----------------|
|**Umieść otwierający nawias klamrowy w nowym wierszu dla funkcji**|Edytor kodu, gdy ta opcja jest zaznaczona, przenosi otwierający nawias klamrowy, skojarzone z funkcją do nowego wiersza.|
|**Umieść otwierający nawias klamrowy w nowym wierszu dla bloków sterowania**|Gdy ta opcja jest zaznaczona, edytora kodu przenosi otwierający nawias klamrowy, skojarzone z bloku sterowania (na przykład `if` i `while` kontrolować bloki) do nowego wiersza.|

## <a name="spacing"></a>Odstępy
 Opcje te określają, jak spacje są dodawane w **źródła**widoku.

## <a name="uielement-list"></a>Lista elementów UI

|Opcja|Opis|
|------------|-----------------|
|**Wstaw spację po ogranicznik przecinkami**|Gdy ta opcja jest zaznaczona, edytora kodu dodaje spację po ograniczniki przecinkami.|
|**Wstaw spację po średniku w instrukcji "for"**|Gdy ta opcja jest zaznaczona, edytora kodu dodaje odstęp po każdym średniku w pierwszym wierszu `for` pętli.|
|**Wstaw spację przed operatorami binarnymi i po**|Gdy ta opcja jest zaznaczona, edytora kodu spację przed operatorami binarnymi i po (na przykład, +, -, & &, &#124; &#124;).|
|**Wstaw spację po słowach kluczowych w instrukcjach przepływu sterowania**|Gdy ta opcja jest zaznaczona, edytora kodu spację po słowach kluczowych JavaScript w instrukcjach przepływu sterowania.|
|**Wstaw spację po — słowo kluczowe funkcji dla funkcji anonimowych.**|Gdy ta opcja jest zaznaczona, edytora kodu spację po `function` dla funkcji anonimowych.|
|**Wstaw spację po otwarciu i przed zamknięciem nawiasy niepusta**|Gdy ta opcja jest zaznaczona, edytora kodu dodaje odstęp po nawiasie otwierającym, a także przed nawiasem zamykającym Jeśli znaki niepustym znajdują się w nawiasie.|

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)