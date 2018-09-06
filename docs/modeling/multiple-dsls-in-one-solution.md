---
title: Wiele języków DSL w jednym rozwiązaniu
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ce16cba80962c68d2480e934e2816be4fe77ab1f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775880"
---
# <a name="multiple-dsls-in-one-solution"></a>Wiele języków DSL w jednym rozwiązaniu
Można spakować kilka języków DSL w ramach jednego rozwiązania, tak, aby zainstalować je ze sobą.

 Kilka technik umożliwia integrowanie wiele języków DSL. Aby uzyskać więcej informacji, zobacz [integrowanie modeli za pomocą programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) i [porady: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md) i [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Aby utworzyć więcej niż jednym języku DSL w tym samym rozwiązaniu

1.  Tworzenie dwóch lub więcej rozwiązań DSL i projekt VSIX, a następnie dodaj wszystkie projekty do jednego rozwiązania.

    -   Aby utworzyć nowy projekt VSIX: W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#**, **rozszerzalności**, **projekt VSIX**.

    -   Utwórz dwa lub więcej rozwiązań DSL w katalogu rozwiązania VSIX.

         Dla każdego języka DSL Otwórz nowe wystąpienie programu Visual Studio. Utwórz nowy język DSL i określić ten sam folder rozwiązania jako rozwiązania VSIX.

         Upewnij się, tworzenie każdego DSL z rozszerzeniem innej nazwy pliku.

    -   Zmiany nazw **Dsl** i **DslPackage** projektów, tak aby były różne. Na przykład: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

    -   W każdym **DslPackage\*\source.extension.tt**, zaktualizować ten wiersz do poprawnej nazwy projektu Dsl:

         `string dslProjectName = "Dsl2";`

    -   W przypadku rozwiązania VSIX Dodaj Dsl * i DslPackage\* projektów.

         Warto umieścić każdej pary w jego własnym folderze rozwiązania.

2.  Łączenie języków DSL manifesty VSIX:

    1.  Otwórz _YourVsixProject_**\source.extension.manifest**.

    2.  Dla każdego języka DSL, wybierz **Dodaj zawartość** i Dodaj:

        -   `Dsl*` projekt jako **składnik MEF**

        -   `DslPackage*` projekt jako **składnik MEF**

        -   `DslPackage*` projekt jako **pakietu programu VS**

3.  Skompiluj rozwiązanie.

 Wynikowy VSIX zainstaluje zarówno językami DSL. Można je przetestować, naciskając klawisz F5 lub wdrożyć _YourVsixProject_**\bin\Debug\\\*.vsix**.

## <a name="see-also"></a>Zobacz też

- [Integrowanie modeli za pomocą Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)