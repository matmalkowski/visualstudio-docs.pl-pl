---
title: "Porady: znajdowanie DLL, która nastąpiła awaria programu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6232f86e9e9f5d59e9e109d08b75120cc90902c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Porady: odnajdywanie biblioteki DLL, w której nastąpiła awaria programu
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz polecenie Import i eksport ustawień w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Jeśli aplikacja ulegnie awarii podczas wywoływania biblioteki DLL systemu lub do kogoś innego kodu, należy znaleźć jaka DLL była aktywna podczas wystąpienia awarii. Jeśli wystąpi awaria w bibliotece DLL poza aplikacji użytkownika, można go zidentyfikować przy użyciu lokalizacji **modułów** okna.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Znajdź, w którym awaria wystąpił podczas korzystania z okna modułów  
  
1.  Należy pamiętać, adres, w których wystąpiła awaria.  
  
2.  Na **debugowania** menu, wybierz **Windows**i kliknij przycisk **modułów**.  
  
3.  W **modułów** oknie Znajdź **adres** kolumny. Konieczne może być umożliwia pasek przewijania jest widoczny.  
  
4.  Kliknij przycisk **adres** u góry kolumny, aby sortować według adresu bibliotek DLL.  
  
5.  Skanowanie posortowaną listę można znaleźć biblioteki DLL, której zakres adresów zawiera lokalizację awarii.  
  
6.  Przyjrzyj się **nazwa** i **ścieżki** kolumn, aby wyświetlić nazwę biblioteki DLL i ścieżkę.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md)   
 [Porady: Korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md)