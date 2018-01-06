---
title: Debugowanie aplikacji trybu mieszanego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2870f1b74532b181ae2101ae01a0e95b494f6f61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-mixed-mode-applications"></a>Debugowanie aplikacji w trybie mieszanym
Aplikacją trybu mieszanego jest każda aplikacja, która łączy w sobie kod natywny (C++) z kodem zarządzanym (takim jak Visual Basic, Visual C# lub C++ działający w środowisku uruchomieniowym języka wspólnego). Debugowanie aplikacji w trybie mieszanym jest przede wszystkim przejrzystości [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; nie jest za bardzo różni się od debugowanie w trybie pojedynczej aplikacji. Istnieje jednak kilka specjalnych okoliczności.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Włącz edycję i kontynuację w języku C++ w debugowaniu trybu mieszanego  
  
-   Aby użyć funkcji edycji i kontynuacji dla C++ w Visual Studio 2013, musisz powrócić do starego aparatu debugowania. Zobacz [przełączanie do trybu zgodności zarządzanej w programie Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) na blogu zarządzania cyklem życia aplikacji firmy Microsoft.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Ocena właściwości aplikacji w trybie mieszanym  
 W aplikacji trybu mieszanego ocena właściwości przez debuger jest kosztowną operacją. W rezultacie operacje debugowania, takie jak przechodzenie mogą, być wykonywane powoli. Aby uzyskać więcej informacji, zobacz [Stepping](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9). W przypadku wystąpienia niskiej wydajności w debugowaniu trybu mieszanego, można wyłączyć oceny właściwości w oknie debugera.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
#### <a name="to-turn-off-property-evaluation"></a>Aby wyłączyć funkcję oceny właściwości  
  
1.  Na **narzędzia** menu, wybierz **opcje**.  
  
2.  W **opcje** po otwarciu okna dialogowego **debugowanie** i wybierz polecenie **ogólne** kategorii.  
  
3.  Wyczyść **Włącz obliczanie właściwości i inne niejawne wywołania funkcji** pole wyboru.  
  
 Ponieważ stosy wywołania natywnego i zarządzanego się różnią, debuger nie zawsze może dostarczyć pełny stos wywołań dla kodu mieszanego. Gdy kod natywny wywołuje kod zarządzany, można zauważyć pewne rozbieżności. Aby uzyskać więcej informacji, zobacz [kod mieszany i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)