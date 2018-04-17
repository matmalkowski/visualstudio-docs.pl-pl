---
title: 'Porady: zmiana budowy katalogu wyjściowego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5a0c4fe60d5092c9226a85ffa561c6fa55a1dfc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-build-output-directory"></a>Porady: zmiana budowy katalogu wyjściowego
Lokalizacja danych wyjściowych można określić na podstawie na konfigurację (dla debugowania, wersji lub obie) wygenerowany przez projekt.  
  
> [!NOTE]
>  Jeśli masz **Instalator** projektu zobacz uwagę na końcu tego artykułu.  
  
## <a name="changing-the-build-output-directory"></a>Zmiana do katalogu wyjściowego kompilacji  
  
#### <a name="to-change-the-build-output-directory"></a>Aby zmienić katalog danych wyjściowych kompilacji  
  
1.  Na pasku menu wybierz **projektu**, *Appname* **właściwości**. Można również przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.  
  
2.  Jeśli projekt Visual Basic, wybierz **skompilować** kartę. W przypadku projektu C#, wybrać **kompilacji** kartę. Jeśli masz projektu C++ lub projektu w języku JavaScript, wybierz **ogólne** kartę.  
  
3.  W konfiguracji listy rozwijanej na górze wybierz konfigurację, której wyjście chcesz zmienić (debugowania, wersji lub wszystkie) lokalizacji pliku.  
  
     Znajdź pozycję Ścieżka danych wyjściowych (**ścieżki wyjściowej kompilacji** w języku Visual Basic **katalog wyjściowy** w programie Visual C++, **ścieżka wyjściowa** w JavaScript i C#). Określ nowy katalog danych wyjściowych kompilacji względem katalogu projektu.  
  
> [!NOTE]
>  W projekcie Instalator **nazwę pliku wyjściowego** okno zmienia lokalizację pliku Setup.exe, a nie lokalizacja plików projektu. Aby uzyskać więcej informacji, zobacz **kompilacji, właściwości konfiguracyjne, okno dialogowe właściwości projektu wdrożenia**.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Ogólna strona właściwości (projekt)](/cpp/ide/general-property-page-project)   
 [Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)