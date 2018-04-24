---
title: 'Porady: debugowanie wprowadzonego kodu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf602d8ee670e5fce8602cb50d2aaa1066b501de
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-injected-code"></a>Porady: Debugowanie wprowadzonego kodu
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz polecenie Import i eksport ustawień w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Przy użyciu atrybutów może bardzo uprościć programowania w języku C++. Aby uzyskać więcej informacji, zobacz [pojęcia](/cpp/windows/attributed-programming-concepts). Niektóre atrybuty są interpretowane bezpośrednio przez kompilator. Inne atrybuty iniekcję kodu do źródła program, który następnie kompiluje kompilatora. Ten kod wprowadzony sprawia, że ułatwia programowanie dzięki zmniejszeniu ilości kodu, który trzeba napisać. Jednak czasami usterki może spowodować niepowodzenie podczas wykonywania wprowadzony kod aplikacji. W takim przypadku prawdopodobnie można przyjrzeć się wprowadzony kod. Program Visual Studio udostępnia dwa sposoby można zobaczyć wprowadzony kod:  
  
-   Możesz wyświetlić wprowadzony kod w **dezasemblacji** okna.  
  
-   Przy użyciu [/Fx](/cpp/build/reference/fx-merge-injected-code), można utworzyć pliku źródłowego scalone, który zawiera oryginalny i wprowadzony kod.  
  
 **Dezasemblacji** okno zawiera instrukcje języka zestawu, które odpowiadają kodu źródłowego i kod wstrzyknięte przez atrybuty. Ponadto **dezasemblacji** okno może zawierać adnotacji kodu źródłowego.  
  
### <a name="to-turn-on-source-annotation"></a>Aby włączyć adnotacji źródła  
  
-   Kliknij prawym przyciskiem myszy **dezasemblacji** okna i wybierz polecenie **wyświetlić kodu źródłowego** z menu skrótów.  
  
     Jeśli znasz lokalizacji atrybutu w oknie źródła, można użyć menu skrótów można znaleźć wprowadzony kod w **dezasemblacji** okna.  
  
### <a name="to-view-injected-code"></a>Aby wyświetlić wprowadzonego kodu  
  
1.  Debuger musi być w trybie przerwania.  
  
2.  W oknie kodu źródłowego umieść kursor na początku atrybut, którego wprowadzony kod, który chcesz wyświetlić.  
  
3.  Kliknij prawym przyciskiem myszy i wybierz **przejść do dezasemblacji** z menu skrótów.  
  
     Jeśli lokalizacja atrybutu zbliża się do bieżącego punkt wykonywania, możesz wybrać **dezasemblacji** w oknie **debugowania** menu.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Aby wyświetlić kod dezasemblacji w bieżącym punkcie wykonywania  
  
1.  Debuger musi być w trybie przerwania.  
  
2.  Z **debugowania** menu, wybierz **Windows**i kliknij przycisk **dezasemblacji**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)