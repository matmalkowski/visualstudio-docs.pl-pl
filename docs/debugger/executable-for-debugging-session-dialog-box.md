---
title: "Plik wykonywalny dla sesji — okno dialogowe debugowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c52d66d0a2e71b96a907fc73b16d42fa13b080bb
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="executable-for-debugging-session-dialog-box"></a>Wykonywalny dla sesji debugowania — Okno dialogowe
To okno dialogowe pojawia się podczas debugowania biblioteki DLL dla których nie pliku wykonywalnego jest określona. Visual Studio nie może bezpośrednio uruchomić biblioteki DLL. Zamiast tego uruchamia określony plik wykonywalny. Biblioteki DLL można debugować wywołanego przez plik wykonywalny.  
  
 **Nazwa pliku wykonywalnego**  
 Wprowadź ścieżkę do pliku wykonywalnego, który wywołuje DLL debugowania.  
  
 **Adres URL, których projekt może być dostęp (tylko serwery ATL)**  
 Jeśli debugujesz ATL DLL serwera, wprowadź adres URL, gdzie można znaleźć projektu.  
  
 Po wpisaniu, te ustawienia są przechowywane w projekcie strony właściwości, dzięki czemu nie trzeba wprowadzać ich ponownie w kolejnych sesjach debugowania. Jeśli trzeba zmienić ustawienia, można otwierać strony właściwości i zmień wartości. Aby uzyskać więcej informacji na temat określania plik wykonywalny dla sesji debugowania, zobacz [debugowanie bibliotek DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)