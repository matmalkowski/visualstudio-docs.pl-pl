---
title: Wbudowanej zmiennej tymczasowej - Refaktoryzacja (C#) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0182179f-f74f-47a2-a1dc-b60c86f9abaf
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6e9ed28a42aa3d7521a059b668eed8ae1d28b8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="inline-a-temporary-variable-with-c"></a>Wbudowanej zmiennej tymczasowej w języku C# #
**Co:** umożliwia usunięcie zmiennej tymczasowej i zamień ją na rzeczywisty kod zamiast tego.

**Kiedy:** użycie zmiennej tymczasowej sprawia, że kod jest trudne do zrozumienia.  

**Dlaczego:** usuwanie zmiennej tymczasowej może czytelność kodu w niektórych sytuacjach

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz zmiennej tymczasowej, aby był śródwierszowy:

   ![Wyróżniony kod](media/inline_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **wbudowanej zmiennej tymczasowej** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **wbudowanej zmiennej tymczasowej** z menu podręcznego okna podglądu.

   Zmienna zostanie usunięta i jego użycia zastąpiony wartością zmiennej natychmiast.

   ![Wynik wbudowany](media/inline_result.png)

## <a name="see-also"></a>Zobacz też  
[Refaktoryzacja (C#)](../refactoring-csharp.md)