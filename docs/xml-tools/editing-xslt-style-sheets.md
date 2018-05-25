---
title: Edytowanie arkuszy stylów XSLT
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f224e91f72d2fa751ddc8b170f78b8859c43f4
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="edit-xslt-style-sheets"></a>Edytowanie arkuszy stylów XSLT

Edytor XML można również edytować arkuszy stylów XSLT. Można wykorzystać domyślny edytor funkcje, takie jak IntelliSense, obramowanie, fragmentów kodu XML i tak dalej. Ponadto istnieją również nowe funkcje, które ułatwiają tworzenie w kodzie XSLT.

## <a name="xslt-features"></a>Funkcje XSLT
 W poniższej tabeli opisano funkcje specyficzne dla pracy z arkuszy stylów XSLT.

 **Kolorowanie składni**

 Słowa kluczowe XSLT, takich jak `template`, `match`i tak dalej są wyświetlane w kolorze — słowo kluczowe XSLT określonego przez **czcionki i kolory** ustawienia.

 **Faliste podkreślenie**

 Edytor XML używa zainstalowana *xslt.xsd* pliku do sprawdzania poprawności arkuszy stylów XSLT. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenie. Edytor XML kompiluje również arkusza stylów w tle i raporty o błędach kompilatora lub ostrzeżenia o odpowiednich faliste podkreślenie.

 **Obsługa blokach skryptu**

 Kod w blokach skryptu jest obsługiwana przez debuger XSLT, dlatego można ustawić punktów przerwania i kroków kod bloku skryptu.

 **Wyświetl dane wyjściowe XSLT**

 Można wykonać przekształcenia XSL i wyświetlić dane wyjściowe z edytora XML. Aby uzyskać więcej informacji, zobacz [porady: wykonywanie transformację XSLT z edytora XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Debugowanie XSLT**

 Można uruchomić debugera XSLT z pliku XSLT w edytorze XML. Debuger obsługuje ustawianie punktów przerwania w pliku XSLT, wyświetlanie stanu wykonania XSLT i tak dalej. Ustawiając kursor nad zmiennej XSLT wywołuje etykietkę zawierającą wartość zmiennej. Debuger może służyć do debugowania arkusz stylów lub debugowanie skompilowanych transformacji XSL wywoływane z innej aplikacji. Aby uzyskać więcej informacji, zobacz [profilowanie XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)