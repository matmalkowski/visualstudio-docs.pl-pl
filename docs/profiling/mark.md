---
title: Oznacz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89a26a3a3729241cb4ec9180e6cb16f131194b86
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844797"
---
# <a name="mark"></a>Znacznik
*VSPerfCmd.exe* **znak** opcja Wstawia informacje podane w pliku danych profilowania. Znak może być wymieniona w raporcie VSPerfReport oddzielne lub w widoku raportu znacznik profilera interfejsu użytkownika. **Oznacz** może służyć do określenia w filtrach, a następnie Wyświetl punkt początkowy i końcowy.  
  
 **Znak** opcja musi być jedyną opcją określona w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametry  
 `MarkID`  
 Zdefiniowane przez użytkownika liczba całkowita, która jest wymieniony jako identyfikator znacznika w raportach i widokach profilera. `MarkID` nie musi być unikatowa.  
  
 `MarkName`  
 (Opcjonalnie) Ciąg zdefiniowane przez użytkownika, który jest wymieniony jako nazwa znacznika w raportach i widokach profilera. Jeśli `MarkName` nie zostanie określony, pole Nazwa znacznika listy znak jest pusty. Należy ująć ciągów, które zawierają spacje lub przekazywania ukośniki ("/") w znaki cudzysłowu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wstawia znacznik z Identyfikatorem 123 i nazwę znacznika "TestMark".  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)