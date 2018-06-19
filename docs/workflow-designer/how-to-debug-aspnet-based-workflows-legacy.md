---
title: 'Projektant przepływu pracy — porady: debugowanie przepływów pracy opartych na programie ASP.NET (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7bf16a6a88c5d4cd063f1c32ca846031d8b2588d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975875"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Porady: debugowanie przepływów pracy opartych na programie ASP.NET (starsze)

W tym temacie opisano, jak do debugowania aplikacji oparty na programie ASP.NET Windows Workflow Foundation (WF) obiektu docelowego albo programu .NET Framework w wersji 3.5 lub WinFX w starszej wersji projektanta przepływów pracy systemu Windows.

Można debugować starszych przepływy pracy, które są uruchamiane w ASP.NET lub starszego przepływów pracy, które są publikowane jako usługę sieci Web przez dołączenie do procesu, w którym jest hostowany przepływ pracy.

## <a name="to-debug-an-aspnet-based-workflow"></a>Aby debugować przepływ pracy oparty na programie ASP.NET

1.  Włącz debugowanie aplikacji ASP.NET przez ustawienie **debug = true** w pliku web.config.

2.  Ustaw jako projekt startowy biblioteki przepływu pracy i ustawić punkty przerwania w przepływie pracy.

3.  Wprowadź adres URL domyślnej strony sieci Web we właściwościach projektu przepływu pracy **debugowania** opcji **Start przeglądarki za pomocą zewnętrznego adresu URL** pola tekstowego.

4.  Wybierz **dołączyć do procesu** na **debugowania** menu.

5.  Wybierz proces, aby dołączyć do z **dostępne procesy** listy.

     Dołączanie do procesu w3wp.exe, webdev.webserver lub aspnet_wp, w którym jest hostowany przepływ pracy.

6.  Kliknij przycisk **wybierz** obok **dołączyć do** pola tekstowego.

     **Wybór typu kodu** zostanie wyświetlone okno dialogowe.

7.  Wybierz **Debuguj te typy kodu** i wybierz **przepływu pracy**.

8.  Kliknij przycisk **OK**.

9. Kliknij przycisk **dołączyć**.

10. Otwórz w przeglądarce domyślnej strony sieci Web i Uruchom przepływ pracy.

## <a name="see-also"></a>Zobacz także

- [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Instrukcje: Ustawianie punktów przerwania w przepływach pracy (starsza wersja)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)