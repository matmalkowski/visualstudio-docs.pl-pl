---
title: "Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać niezaufaną komendę | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21daec7113462221b392b5f29b1604a24fe5c74c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać niezaufaną komendę
To okno dialogowe Ostrzeżenie pojawia się podczas korzystania z serwera źródłowego. Wskazuje on, że polecenie debuger musi wykonać uzyskanie kodu źródłowego nie jest na liście zaufanych polecenia zawarte w pliku srcsvr.ini serwera źródłowego. Jeśli jest to prawidłowe polecenie, można dodać go do pliku srcsvr.ini. W przeciwnym razie nie należy uruchamiać go. Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Tekst komunikatu  
 **Debuger musi wykonać następujące polecenie niezaufanych uzyskanie kodu źródłowego z serwera źródłowego.**  
  
 **Jeśli plik symboli debugowania (\*.pdb) jest nie ze znanego i zaufanego źródła, to polecenie może być nieprawidłowy lub niebezpiecznych do uruchomienia.**  
  
 **Czy chcesz uruchomić to polecenie?**  
  
## <a name="uielement-list"></a>Lista elementów UI  
 Pole tekstowe  
 Polecenie z pliku PDB do uruchomienia.  
  
 Uruchom  
 Zezwalaj na polecenie do uruchomienia.  
  
 Nie uruchamiaj  
 Zatrzymaj wykonywanie polecenia i pobieranie plików z serwera źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Serwer źródłowy](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)