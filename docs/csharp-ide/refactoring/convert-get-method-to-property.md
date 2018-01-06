---
title: "Konwertuj metody Get właściwości — Refaktoryzacja (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 71ff3db81be256bdb82413d04b2f939b706c6586
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Konwertuj metody Get właściwości / przekonwertować właściwości metody Get
## <a name="convert-get-method-to-property"></a>Konwertuj metody Get właściwości
**Co:** pozwala konwertować metody Get właściwości (i opcjonalnie Set, metoda) i na odwrót.

**Kiedy:** ma metody Get, który nie zawiera żadnych logiki.

**Jak:**

1. Umieść kursor w nazwie metody Get.

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **zastąpić metodę właściwości** z menu podręcznego okna podglądu. Jeśli masz metody Set, wybierając można przekonwertować również Set, metoda w tym momencie **metody Zastąp Get i Set, metoda z właściwością**.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **zastąpić metodę właściwości** z menu podręcznego okna podglądu. Jeśli masz metody Set, wybierając można przekonwertować również Set, metoda w tym momencie **metody Zastąp Get i Set, metoda z właściwością**.

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

**Jak:**

1. Umieść kursor w nazwie metody Get.

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **zastąpić właściwość metody** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **zastąpić właściwość metody** z menu podręcznego okna podglądu.

1. Jeśli są zadowalające, zmiany w podglądzie kodu, naciśnij klawisz **Enter** lub kliknij przycisk Napraw z menu i zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz też  
[Refaktoryzacja (C#)](../refactoring-csharp.md)  
[Podgląd zmian](../../ide/preview-changes.md)