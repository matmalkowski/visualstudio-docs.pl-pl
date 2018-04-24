---
title: Debugowanie skryptu po stronie klienta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f31897cc4fb48fd7c814d4d25cb41ce0cb7e57da
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="client-side-script-debugging"></a>Debugowanie skryptu po stronie klienta
Debuger programu Visual Studio oferuje kompleksowe środowisko debugowania Znajdowanie i usuwanie błędów skryptów po stronie klienta w stron ASP.NET.  
  
## <a name="opening-script-documents"></a>Otwieranie dokumentów skryptu  
Można zobaczyć listy dokumentów skryptu po stronie serwera i klienta w **Eksploratora rozwiązań** do wyświetlenia. Można otworzyć dokumentu skryptu z **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie dokumentów skryptu](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Mapowanie punktów przerwania  
 W programie Visual Studio nie może bezpośrednio debugowania kodu po stronie serwera, ale można ustawić punktu przerwania w pliku po stronie serwera. Visual Studio automatycznie mapuje punkt przerwania w odpowiedniej lokalizacji w pliku po stronie klienta i tworzy zamapowanych punktu przerwania w kodzie po stronie klienta.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Ręczne lub automatyczne dołączanie do skryptu  
 Aby rozpocząć debugowanie skryptów w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dołączyć debuger skrypt, którego chcesz debugować. Przyczyną może być ręczne lub automatyczne.  
  
 Możesz ręcznie dołączyć za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu debugera do uruchomionego procesu skryptu, aby dołączyć do wyboru. Aby uzyskać więcej informacji, zobacz [porady: dołączanie do skryptu](../debugger/how-to-attach-to-script.md).  
  
 Debuger automatyczne dołączenie do skryptu, gdy wystąpi jedno z następujących czynności:  
  
-   Możesz trafiony punkt przerwania ustawiony w skrypcie.  
  
-   Trafienia skrypt VBScript `Stop` instrukcji lub JScript `debugger` instrukcji w kodzie skryptu.  
  
-   W przeglądarce lub na serwerze napotka składnię, lub uruchom błąd w skrypcie. W takim przypadku okno dialogowe zostanie wyświetlone i mieć opcję, aby rozpocząć debugowanie.  
  
 Ręcznie dołączania do skryptu, proces skryptu będzie działać, dopóki aplikacja jest zatrzymywane. Zatrzymanie go, wybierając **Podziel** na **debugowania** menu.  
  
 Gdy debuger dołącza automatycznie, wykonywanie skryptu jest zatrzymywane w wierszu gdzie punkt przerwania, `Stop` instrukcji lub `debugger` instrukcji lub błąd wystąpił, lub w momencie, gdy została wybrana opcja można rozpocząć debugowania w programie Internet Explorer.  
  
 W tym momencie można urządzenia debugera normalne rozpocząć debugowanie. Na przykład można użyć **krok** poleceń, aby kontynuować jego wykonywanie kodu wiersz po wierszu. Można użyć **stos wywołań** okno widoku oraz kontroli skryptu przepływu. Można użyć zmiennej windows lub **Immediate** okno, aby wyświetlić lub zmienić właściwości i zmiennych.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Ulepszone komunikaty do debugowania skryptów  
 Program Visual Studio oferuje rozszerzone komunikaty dla typowych skryptu debugowania problemów. Te komunikaty nie są wyświetlane, chyba że dołączyć do programu Internet Explorer ręcznie. Jeśli wystąpi błąd podczas programu Internet Explorer jest otwierana automatycznie, spróbuj ręcznie dołączania, dzięki czemu można wyświetlić komunikaty o błędach.  
  
## <a name="debugging-ajax-script-applications"></a>Debugowanie aplikacji skryptów AJAX  
 Aplikacje sieci Web z włączoną obsługą technologii AJAX w znacznym stopniu wykorzystywane kodu skryptu i stanowić specjalne wyzwania debugowania. Aby uzyskać informacji na temat metod debugowania AJAX zobacz  
  
 [Debugowanie i śledzenie — Przegląd aplikacji Ajax](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Ograniczenia debugowania skryptu](../debugger/limitations-on-script-debugging.md)   
 [Zmienne systemu Windows](../debugger/debugger-windows.md)   
 [Okno bezpośrednie](../ide/reference/immediate-window.md)   
 [Debugowanie i śledzenie — Przegląd aplikacji Ajax](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
