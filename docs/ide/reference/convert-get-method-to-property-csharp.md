---
title: "Konwertuj metody Get właściwości i przekonwertowanie właściwości na metodę Get w języku C# | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: a23af31c5099908ed0b6fed07404216a57975f75
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
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

## <a name="see-also"></a>Zobacz także

[Refaktoryzacja](../refactoring-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)