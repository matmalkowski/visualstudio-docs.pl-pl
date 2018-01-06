---
title: Oznacz | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8fb616cd9b938bb2624d762272f98ae2ad1f7fe9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mark"></a>Znacznik
VSPerfCmd.exe **znak** opcja Wstawia informacje podane w pliku danych profilowania. Znak może być wymieniona w raporcie VSPerfReport oddzielne lub w widoku raportu znacznik profilera interfejsu użytkownika. **Oznacz** może służyć do określenia w filtrach, a następnie Wyświetl punkt początkowy i końcowy.  
  
 **Znak** opcja musi być jedyną opcją określona w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametry  
 `MarkID`  
 Zdefiniowane przez użytkownika liczba całkowita, która jest wymieniony jako identyfikator znacznika w raportach i widokach profilera. `MarkID`nie musi być unikatowa.  
  
 `MarkName`  
 (Opcjonalnie) Ciąg zdefiniowane przez użytkownika, który jest wymieniony jako nazwa znacznika w raportach i widokach profilera. Jeśli `MarkName` nie zostanie określony, pole Nazwa znacznika listy znak jest pusty. Należy ująć ciągów, które zawierają spacje lub przekazywania ukośniki ("/") w znaki cudzysłowu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wstawia znacznik z Identyfikatorem 123 i nazwę znacznika "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)