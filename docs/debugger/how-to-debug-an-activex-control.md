---
title: 'Porady: debugowanie formantu ActiveX | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 932ccf7bdbea8fa68d0c2883d0ae8fd77eedf5bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-an-activex-control"></a>Porady: debugowanie kontrolki ActiveX
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz polecenie Import i eksport ustawień w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Debugowanie formantu ActiveX, należy określić (wykonywalnego) używany do uruchamiania w kontenerze.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Aby określić kontener dla sesji debugowania  
  
1.  W Eksploratorze rozwiązań wybierz projekt.  
  
2.  Z **widoku** menu, wybierz **strony właściwości**.  
  
3.  W **stron właściwości projektów** po otwarciu okna dialogowego **właściwości konfiguracji** folder, a następnie wybierz **debugowanie**.  
  
4.  W obszarze **debugowanie** kategorii, zlokalizuj **polecenia** właściwości.  
  
5.  Określ nazwę ścieżka kontenera. Na przykład C:\Program Files\Internet Explorer\IEXPLORE. WYWOŁANIE PLIKU EXE.  
  
6.  Jeśli używasz aktywnego pulpitu programu Internet Explorer można określić jako kontener, wpisz `/new` w **argumenty polecenia** pole.  
  
7.  Kliknij przycisk **OK**.  
  
     Jeśli nie określisz kontenera w **stron właściwości projektów** okno dialogowe, można określić kontenera po rozpoczęciu debugowania. Po wybraniu polecenia wykonywania można uruchomić debugowania, [plik wykonywalny debugowania — okno dialogowe sesji](../debugger/executable-for-debugging-session-dialog-box.md) pojawi się. Określ nazwę ścieżka kontenera, w oknie dialogowym.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX](/cpp/mfc/activex-controls)   
 [Testowanie właściwości i zdarzeń za pomocą kontenera testu](/cpp/mfc/testing-properties-and-events-with-test-container)   
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)   
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)