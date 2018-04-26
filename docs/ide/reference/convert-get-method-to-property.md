---
title: Konwertuj metody Get właściwości i przekonwertowanie właściwości na metodę Get w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: douge
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 291f7a52bfbb702960259e2643967ff0a8e782dc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Konwertuj metody Get właściwości / przekonwertować właściwości refaktoryzacje metody Get

Refaktoryzacje te dotyczą:

- C#

## <a name="convert-get-method-to-property"></a>Konwertuj metody Get właściwości

**Co:** pozwala konwertować metody Get właściwości (i opcjonalnie Set, metoda) i na odwrót.

**Kiedy:** ma metody Get, który nie zawiera żadnych logiki.

### <a name="how-to"></a>Porada

1. Umieść kursor w nazwie metody Get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **zastąpić metodę właściwości** z menu podręcznego okna podglądu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **zastąpić metodę właściwości** z menu podręcznego okna podglądu.

1. (Opcjonalnie) Jeśli masz metody Set, wybierając można przekonwertować również Set, metoda w tym momencie **metody Zastąp Get i Set, metoda z właściwością**.

1. Jeśli są zadowalające, zmiany w podglądzie kodu, naciśnij klawisz **Enter** lub kliknij przycisk Napraw z menu i zmiany zostaną zatwierdzone.

Przykład:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Konwertuj właściwość metody Get

**Co:** służy do konwertowania właściwości na metodę Get

**Kiedy:** ma właściwość, która obejmuje więcej niż natychmiast ustawiania i pobierania wartości

### <a name="how-to"></a>Porada

1. Umieść kursor w nazwie metody Get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **zastąpić właściwość metody** z menu podręcznego okna podglądu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **zastąpić właściwość metody** z menu podręcznego okna podglądu.

1. Jeśli są zadowalające, zmiany w podglądzie kodu, naciśnij klawisz **Enter** lub kliknij przycisk Napraw z menu i zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)