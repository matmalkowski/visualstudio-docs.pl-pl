---
title: 'Porady: zmiana budowy katalogu wyjściowego'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 721b8241a3278ddbf1be3b5477e8829b7aa4447b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942250"
---
# <a name="how-to-change-the-build-output-directory"></a>Porady: zmiana budowy katalogu wyjściowego

Lokalizacja danych wyjściowych można określić na podstawie na konfigurację (dla debugowania, wersji lub obie) wygenerowany przez projekt.

> [!NOTE]
> Jeśli masz **Instalator** projektu, zobacz uwagę na końcu tego artykułu.

## <a name="change-the-build-output-directory"></a>Zmiana budowy katalogu wyjściowego

1.  Na pasku menu wybierz **projektu** > **\<nazwa_aplikacji > właściwości**. Można również przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.

2.  Jeśli projekt Visual Basic, wybierz **skompilować** kartę. W przypadku projektu C#, wybrać **kompilacji** kartę. Jeśli masz projektu C++ lub projektu w języku JavaScript, wybierz **ogólne** kartę.

3.  W konfiguracji listy rozwijanej na górze wybierz konfigurację, której wyjście chcesz zmienić (debugowania, wersji lub wszystkie) lokalizacji pliku.

     Znajdź pozycję Ścieżka danych wyjściowych (**ścieżki wyjściowej kompilacji** w języku Visual Basic **katalog wyjściowy** w programie Visual C++, **ścieżka wyjściowa** w JavaScript i C#). Określ nowy katalog danych wyjściowych kompilacji względem katalogu projektu.

> [!NOTE]
> W projekcie Instalator **nazwę pliku wyjściowego** okno zmienia tylko lokalizacja *Setup.exe* pliku nie lokalizacji plików projektu. Aby uzyskać więcej informacji, zobacz **kompilacji, właściwości konfiguracyjne, okno dialogowe właściwości projektu wdrożenia**.

## <a name="see-also"></a>Zobacz także

- [Strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Strona Ogólne właściwości (projekt)](/cpp/ide/general-property-page-project)
- [Kompilowanie i kompilacji](../ide/compiling-and-building-in-visual-studio.md)