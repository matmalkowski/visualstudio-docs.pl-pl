---
title: 'Porady: debugowanie w trybie mieszanym | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce056b60a3e080490a2ad60f4aee5a7b5c8dd63
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633526"
---
# <a name="how-to-debug-in-mixed-mode"></a>Porady: debugowanie w trybie mieszanym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: debugowanie w trybie mieszanym](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-in-mixed-mode).  
  
W poniższych procedurach opisano sposób debugowania kodu zarządzanego i natywnego, tzw. debugowanie w trybie mieszanym. Istnieją dwa scenariusze, aby to zrobić, w zależności od tego, czy biblioteka DLL lub w aplikacji są zapisywane w kodzie natywnym:  
  
-   Aplikacja wywołująca, która wywołuje bibliotekę DLL są zapisywane w kodzie natywnym. W tym przypadku jest zarządzana biblioteka DLL i debugery zarówno zarządzanego i natywnego musi być włączona debugować oba. Można to sprawdzić  **\<Projekt > strony właściwości** okno dialogowe. Jak to zrobić, zależy od tego, czy rozpoczynasz debugowanie z projektu DLL lub wywoływania projektu aplikacji.  
  
-   Aplikacja wywołująca, która wywołuje bibliotekę DLL są zapisywane w kodzie zarządzanym i biblioteki DLL są zapisywane w kodzie natywnym.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Aby włączyć debugowanie w trybie mieszanym  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt.  
  
2.  Na **widoku** menu, kliknij przycisk **stron właściwości**.  
  
3.  W  **\<Projekt > strony właściwości** okna dialogowego rozwiń **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.  
  
4.  Ustaw **typ debugera** do **mieszane** lub **automatycznie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md)



