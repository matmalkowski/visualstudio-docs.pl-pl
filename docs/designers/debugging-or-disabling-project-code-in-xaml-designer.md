---
title: "Debugowanie lub wyłączenie kodu projektu w Projektancie XAML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: bbfe3eb4f76d8237d6e1a1b7c26aa48b1f081f1e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>Debugowanie lub wyłączenie kodu projektu w Projektancie XAML
W wielu przypadkach nieobsługiwanych wyjątków w Projektancie XAML może być spowodowane przez kod projektu próbujących uzyskać dostęp do właściwości lub metody, które zwracać różne wartości i pracować na różne sposoby, gdy aplikacja jest uruchomiona w projektancie. Rozwiąż te wyjątki, debugowanie kodu projektu w innym wystąpieniu programu Visual Studio lub czasowo uniemożliwić ich po wyłączeniu kodu projektu w projektancie.  
  
 Zawiera kod projektu:  
  
-   Niestandardowe formanty i użytkownika  
  
-   Biblioteki klas  
  
-   Konwertery wartości  
  
-   Powiązania danych czasu projektowania wygenerowane z kodu projektu  
  
 Po wyłączeniu kodu projektu programu Visual Studio będzie Pokaż symbole zastępcze takie jak nazwa właściwości do wiązania, gdy dane nie są już niedostępne; lub symbol zastępczy dla formantu, który nie jest już uruchomiony.  
  
 ![Nieobsługiwany wyjątek w oknie dialogowym](../designers/media/xaml_unhandledexception.png "XAML_UnhandledException")  
  
#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Aby określić, czy kod projektu powoduje Wystąpił wyjątek  
  
1.  W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby załadować ponownie projektanta** łącza.  
  
2.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** Aby skompilować i uruchomić aplikację.  
  
     Jeśli aplikacja tworzy i zostanie wykonane pomyślnie, wyjątek czasu projektowania może być spowodowane przez kod działa w Projektancie projektu.  
  
#### <a name="to-debug-project-code-running-in-the-designer"></a>Aby debugować kod projektu działający w Projektancie  
  
1.  W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i załadować ponownie projektanta** łącza.  
  
2.  W Menedżerze zadań systemu Windows, zaznacz opcję **Zakończ zadanie** przycisk, aby zamknąć wszystkie wystąpienia projektanta XAML programu Visual Studio, które są aktualnie uruchomione.  
  
     ![Wystąpienia projektanta XAML w Menedżer zadań](../designers/media/xaml_taskmanager.png "XAML_TaskManager")  
  
3.  W programie Visual Studio Otwórz strony XAML, który zawiera kod lub formant, który chcesz debugować.  
  
4.  Otwórz nowe wystąpienie programu Visual Studio, a następnie otwórz drugie wystąpienie projektu.  
  
5.  Ustaw punkt przerwania w kodzie projektu.  
  
6.  W nowym wystąpieniu programu Visual Studio na pasku menu wybierz opcję **debugowania**, **dołączyć do procesu**.  
  
7.  W **dołączyć do procesu** okna dialogowego, w **dostępne procesy** wybierz **XDesProc.exe**, a następnie wybierz pozycję **Attach** przycisk.  
  
     ![Proces projektanta XAML](../designers/media/xaml_attach.png "XAML_Attach")  
  
     Jest to proces projektanta XAML w pierwszym wystąpieniu programu Visual Studio.  
  
8.  W pierwszym wystąpieniu programu Visual Studio, na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**.  
  
     Można teraz przejść do kodu, w którym jest uruchomiony w projektancie.  
  
#### <a name="to-disable-project-code-in-the-designer"></a>Aby wyłączyć kodu projektu w Projektancie  
  
-   W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i załadować ponownie projektanta** łącza.  
  
-   Można również na pasku narzędzi w Projektancie XAML, wybierz **Wyłącz kod projektu** przycisku.  
  
     ![Przycisk Wyłącz kod projektu](../designers/media/xaml_disablecode.png "XAML_DisableCode")  
  
     Można przełączyć przycisk ponownie, aby ponownie włączyć kod projektu.  
  
    > [!NOTE]
    >  W projektach przeznaczonych dla ARM lub X64 procesorów, Visual Studio nie można uruchomić kod projektu w projektancie, więc **Wyłącz kod projektu** przycisk jest niedostępny w projektancie.  
  
-   Jedną z opcji spowoduje, że projektanta, aby załadować ponownie, a następnie będzie Wyłącz cały kod skojarzony projekt.  
  
    > [!NOTE]
    >  Wyłączanie kodu projektu może prowadzić do utraty danych czasu projektowania. Alternatywą jest do debugowania kodu uruchamianego w projektancie.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)