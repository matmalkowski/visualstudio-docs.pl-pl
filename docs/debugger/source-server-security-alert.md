---
title: "Alarm zabezpieczeń serwera źródłowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eb50bec1967b9c1f7a969eb802888864f5e72eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="source-server-security-alert"></a>Alarm zabezpieczeń serwera źródłowego
Korzystając z serwera źródłowego, należy używać tylko plików symboli ze znanej i zaufanej lokalizacji.  
  
 To ostrzeżenie jest wyświetlane, gdy można włączyć obsługę serwera źródłowego. Poleceniom serwera źródłowego są osadzone w pliki symboli debugowania (***.pdb** plików). Upewnij się, że wiadomo, skąd plików PDB.  
  
> [!IMPORTANT]
>  Następujące potencjalne zagrożenia bezpieczeństwa należy brane pod uwagę podczas korzystania z serwera źródłowego: dowolnego polecenia mogą być osadzone w pliku PDB aplikacji, dlatego upewnij się, możesz umieścić tylko te, które ma być wykonane w pliku srcsrv.ini. Każda próba wykonania polecenia nie w pliku srcsvr.ini spowoduje pojawienie się okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: debuger musi wykonać niezaufaną komendę](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nie jest sprawdzana na parametry poleceń, więc należy uważać za pomocą polecenia zaufanych. Na przykład, jeśli użytkownik zaufał narzędziu cmd.exe, złośliwy użytkownik może określić parametry, które czyniłyby polecenie niebezpiecznym.  
  
## <a name="see-also"></a>Zobacz też  
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Serwer źródłowy](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)