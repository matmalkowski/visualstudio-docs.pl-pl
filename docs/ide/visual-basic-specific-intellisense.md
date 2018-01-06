---
title: Visual Basic IntelliSense | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e99bda20d8591f314a75ee74e1b162e5fd64be81
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="intellisense-for-visual-basic-code-files"></a>IntelliSense dla plików kodu programu Visual Basic

Edytor kodu źródłowego języka Visual Basic oferuje następujące funkcje IntelliSense:

## <a name="syntax-tips"></a>Porady dotyczące składni

Porady dotyczące składni Wyświetlanie składni instrukcji, która wpisywania. Jest to przydatne dla instrukcji takich jak [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Automatyczne uzupełnianie

- Ukończenia różnych słów kluczowych

     Na przykład jeśli wpiszesz `goto` i miejsca, IntelliSense wyświetla listę etykiet zdefiniowanych w menu rozwijanym. Obejmują innych obsługiwanych słów kluczowych `Exit`, `Implements`, `Option`, i `Declare`.

- Ukończenia `Enum` i`Boolean`

    Po instrukcji będzie odwoływać się do elementu członkowskiego wyliczenia, IntelliSense wyświetla listę elementów członkowskich `Enum`. Po instrukcji odnoszą się do `Boolean`, IntelliSense wyświetla menu rozwijanego PRAWDA / FAŁSZ.

Uzupełnianie można wyłączyć domyślnie przez wyłączenie **automatyczna lista członków** z **ogólne** stronę właściwości w **Visual Basic** folderu.

Uzupełnianie można wywołać ręcznie za pomocą listy elementów członkowskich, całe słowo lub ALT + Strzałka w prawo. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>IntelliSense w strefie

IntelliSense w strefie pomaga deweloperów języka Visual Basic, którzy muszą wdrażać aplikacje za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i są ograniczone do ustawień częściowej relacji zaufania. Ta funkcja:

- Umożliwia wybranie uprawnienia, których aplikacja będzie uruchamiana z.

- Interfejsy API wyświetlania w wybranej strefy jako dostępne w elementach członkowskich listy, a następnie wyświetlić interfejsów API, które wymagają dodatkowych uprawnień jako niedostępny.

Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Filtrowane listy uzupełniania

W języku Visual Basic liście uzupełniania IntelliSense mają dwa formanty karty znajduje się w dolnej części listy. **Wspólnej** kartę, która jest domyślnie zaznaczone, zawiera elementy, które są najczęściej używane do wykonania instrukcji, która pisania. **Wszystkie** karcie są wyświetlane wszystkie elementy, które są dostępne do automatycznego uzupełniania, łącznie z tymi, które są również na **wspólnej** kartę.

## <a name="see-also"></a>Zobacz także

[Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)