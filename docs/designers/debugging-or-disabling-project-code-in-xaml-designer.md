---
title: Debugowania lub wyłącz kod projektu w Projektancie XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 9d77aa1d776352edd3a030507bc25086cad47d58
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>Debugowania lub wyłącz kod projektu w Projektancie XAML

W wielu przypadkach nieobsługiwanych wyjątków w Projektancie XAML może być spowodowane przez kod projektu próby dostępu do właściwości lub metody zwracać różne wartości lub działa w inny sposób, gdy aplikacja działa w projektancie. Rozwiąż te wyjątki, debugowanie kodu projektu w innym wystąpieniu programu Visual Studio lub czasowo uniemożliwić wyjątki po wyłączeniu kodu projektu w projektancie.

Zawiera kod projektu:

-   Niestandardowe formanty i użytkownika

-   Biblioteki klas

-   Konwertery wartości

-   Powiązania danych czasu projektowania wygenerowane z kodu projektu

Po wyłączeniu kodu projektu programu Visual Studio zawiera symbole zastępcze. Na przykład Visual Studio zawiera nazwę właściwości dla powiązania, których danych nie jest już dostępny, lub symbolem zastępczym dla formantu, który nie jest już uruchomiony.

![Nieobsługiwany wyjątek w oknie dialogowym](../designers/media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Aby określić, czy kod projektu powoduje Wystąpił wyjątek

1.  W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby załadować ponownie projektanta** łącza.

2.  Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie** Aby skompilować i uruchomić aplikację.

     Jeśli aplikacja tworzy i zostanie wykonane pomyślnie, wyjątek czasu projektowania może być spowodowane przez kod działa w Projektancie projektu.

## <a name="to-debug-project-code-running-in-the-designer"></a>Aby debugować kod projektu działający w Projektancie

1.  W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i załadować ponownie projektanta** łącza.

2.  W Menedżerze zadań systemu Windows, zaznacz opcję **Zakończ zadanie** przycisk, aby zamknąć wszystkie wystąpienia projektanta XAML programu Visual Studio, które są aktualnie uruchomione.

     ![Wystąpienia projektanta XAML w Menedżer zadań](../designers/media/xaml_taskmanager.png)

3.  W programie Visual Studio Otwórz strony XAML, który zawiera kod lub formant, który chcesz debugować.

4.  Otwórz nowe wystąpienie programu Visual Studio, a następnie otwórz drugie wystąpienie projektu.

5.  Ustaw punkt przerwania w kodzie projektu.

6.  W nowym wystąpieniu programu Visual Studio na pasku menu wybierz opcję **debugowania** > **dołączyć do procesu**.

7.  W **dołączyć do procesu** okna dialogowego, w **dostępne procesy** wybierz **XDesProc.exe**, a następnie wybierz pozycję **Attach** przycisk.

     ![Proces projektanta XAML](../designers/media/xaml_attach.png)

     Jest to proces projektanta XAML w pierwszym wystąpieniu programu Visual Studio.

8.  W pierwszym wystąpieniu programu Visual Studio, na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**.

     Można teraz przejść do kodu, w którym jest uruchomiony w projektancie.

## <a name="to-disable-project-code-in-the-designer"></a>Aby wyłączyć kodu projektu w Projektancie

-   W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i załadować ponownie projektanta** łącza.

-   Można również na pasku narzędzi w Projektancie XAML, wybierz **Wyłącz kod projektu** przycisku.

     ![Przycisk Wyłącz kod projektu](../designers/media/xaml_disablecode.png)

     Można przełączyć przycisk ponownie, aby ponownie włączyć kod projektu.

    > [!NOTE]
    > W projektach przeznaczonych dla ARM lub X64 procesorów, Visual Studio nie można uruchomić kod projektu w projektancie, więc **Wyłącz kod projektu** przycisk jest niedostępny w projektancie.

-   Jedną z opcji spowoduje, że projektanta, aby załadować ponownie, a następnie będzie Wyłącz cały kod skojarzony projekt.

    > [!NOTE]
    > Wyłączanie kodu projektu może prowadzić do utraty danych czasu projektowania. Alternatywą jest do debugowania kodu uruchamianego w projektancie.

## <a name="see-also"></a>Zobacz także

- [Projekt XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)