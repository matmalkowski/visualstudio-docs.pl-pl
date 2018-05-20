---
title: Zrefaktoryzuj kod, aby zastąpić var jawnego typu
ms.date: 05/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 9d816921f3449edfcd28a2fa9f4e2af9b9d015f9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refaktoryzacja należy zastąpić var jawnego typu

Użyj tego refaktoryzacji, aby zamienić [var](/dotnet/csharp/language-reference/keywords/var) w deklaracji zmiennej lokalnej z typem jawnym.

Dotyczy to refaktoryzacji:

- C#

## <a name="why-to-use-an-explicit-type"></a>Dlaczego Użyj jawnego typu

Poniżej przedstawiono niektóre przyczyny w celu zadeklarowania zmiennej z typem jawnym:

- Aby poprawić czytelność kodu.

- Jeśli nie chcesz zainicjować zmiennej w deklaracji.

Jednak [var](/dotnet/csharp/language-reference/keywords/var) należy użyć, gdy zmienna jest zainicjowana z typu anonimowego, a właściwości obiektu są dostępne w późniejszym czasie. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Jak z niego korzystać

1. Umieść karetkę na `var` — słowo kluczowe.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikona śrubokręt](../media/screwdriver-icon.png) ikony na marginesie pliku kodu.

   ![Użyj menu Szybkie akcje typu jawnego](media/use-explicit-type.png)

1. Wybierz **Użyj jawnego typu**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

## <a name="see-also"></a>Zobacz także

- [Niejawnie wpisane zmienne (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)