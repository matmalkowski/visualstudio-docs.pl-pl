---
title: Alarm zabezpieczeń serwera źródłowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 826669924cc538a63d61ffe5051aa32152a6152d
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511176"
---
# <a name="source-server-security-alert"></a>Alarm zabezpieczeń serwera źródłowego
Podczas korzystania z serwera źródłowego, należy używać tylko plików symboli ze znanych i zaufanych lokalizacji.  
  
 To ostrzeżenie jest wyświetlane po włączeniu obsługi serwera źródłowego. Polecenia serwera źródłowego są osadzone w pliki symboli debugowania (***.pdb** plików). Upewnij się, że wiesz skąd pochodzą pliki PDB.  
  
> [!IMPORTANT]
>  Następujące potencjalne zagrożenia bezpieczeństwa musi być brana pod uwagę podczas korzystania z serwera źródłowego: dowolne polecenia mogą być osadzone w pliku PDB aplikacji, dlatego upewnij się, że możesz umieścić tylko te, które chcesz wykonać w pliku srcsrv.ini. Każda próba wykonania polecenia nie w pliku srcsvr.ini spowoduje pojawienie się okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nie jest sprawdzana poprawność parametrów poleceń, więc należy być ostrożnym z poleceniami zaufanymi. Na przykład, jeśli użytkownik zaufał narzędziu cmd.exe, złośliwy użytkownik może określić parametry, które czyniłyby polecenie niebezpiecznym.  
  
## <a name="see-also"></a>Zobacz też  
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Serwer źródłowy](/windows/desktop/Debug/source-server-and-source-indexing)
