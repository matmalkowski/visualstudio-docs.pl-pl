---
title: 'Porady: Konfigurowanie projektów do platform docelowych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f5f5552cb87f1c8b4501930f23765143a9e9399
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Porady: Konfigurowanie projektów do platform docelowych

Program Visual Studio umożliwia konfigurowanie aplikacji pod kątem różnych platform, w tym platformach 64-bitowych. Aby uzyskać więcej informacji dotyczących obsługi 64-bitowej platformy w programie Visual Studio, zobacz [aplikacji 64-bitowych](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).

## <a name="target-platforms-with-the-configuration-manager"></a>Platformy docelowe z programu Configuration Manager

**Programu Configuration Manager** pozwala szybko dodać nowa platforma do obiektu docelowego projektu. W przypadku wybrania jednej z platform uwzględnionych w programie Visual Studio, aby skompilować projekt dla wybranej platformy są modyfikacji właściwości projektu.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Aby skonfigurować projekt pod kątem platformy 64-bitowych

1.  Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**.

2.  W **platformy aktywne rozwiązanie** listy, wybierz 64-bitowej platformy dla rozwiązania do obiektu docelowego, a następnie wybierz pozycję **Zamknij** przycisku.

    1.  Jeśli nie ma platformy, które mają **platformy aktywne rozwiązanie** wybierz **nowy**.

         **Nowa platforma rozwiązania** zostanie wyświetlone okno dialogowe.

    2.  W **wpisz lub wybierz Nowa platforma** wybierz **x64**.

        > [!NOTE]
        >  Jeśli konfigurację Podaj nową nazwę, należy zmodyfikować ustawienia w **projektanta projektu** pod kątem poprawne platformy.

    3.  Jeśli chcesz skopiować ustawienia z bieżącej konfiguracji platformy, wybierz go, a następnie wybierz **OK** przycisku.

Właściwości dla wszystkich projektów przeznaczonych dla platformy 64-bitowej są aktualizowane i następnej kompilacji projektu zostanie zoptymalizowana dla platformy 64-bitowych.

## <a name="target-platforms-in-the-project-designer"></a>Platformy docelowe w Projektancie projektu

**Projektanta projektu** także sposób pod kątem różnych platform z projektu. W przypadku wybrania jednej z platform uwzględnione na liście w **nowa platforma rozwiązania** okno dialogowe nie działa w przypadku rozwiązania, można utworzyć nazwy konfiguracji niestandardowej i zmodyfikuj ustawienia w **Projektant projektu**  pod kątem poprawne platformy.

Wykonanie tego zadania zależy od języka programowania, którego używasz. Zobacz poniższe łącza, aby uzyskać więcej informacji:

-   Aby uzyskać [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów, zobacz [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

-   Aby uzyskać [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów, zobacz [strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

-   Aby uzyskać [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów, zobacz [/CLR (kompilacja środowiska CLR)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="see-also"></a>Zobacz także

- [Informacje o platformach kompilacji](../ide/understanding-build-platforms.md)
- [/ platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64-bit — aplikacje](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)
- [Techniczną usługi Visual Studio IDE 64-bitowych](../ide/visual-studio-ide-64-bit-support.md)
