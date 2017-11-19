---
title: AutoMark | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc5ad59520f8533527f5c17f6be4b04ad860f2d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="automark"></a>AutoMark
**AutoMark** opcji określa liczbę milisekund między zbierania zdarzeń liczników wydajności oprogramowania systemu Windows. Liczniki wydajności systemu Windows są określone w **WinCounter** opcji.  
  
 Tylko jeden **AutoMark** opcję można określić w wierszu polecenia. Należy pamiętać, że **WinCounter** interwał próbkowania określony przez **AutoMark** jest niezależna od interwał próbkowania głównego.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>Parametry  
 `Milliseconds`  
 Określa liczbę milisekund między operacjami zbierania zdarzeń liczników wydajności systemu Windows.  
  
## <a name="required-options"></a>Wymagane opcje  
 **WinCounter:**`Path`  
 Określa licznik wydajności systemu Windows do zbierania. Korzystając z metody instrumentacji, można określić wiele liczników systemu Windows. Korzystając z metody pobierania próbek, można określić tylko jeden licznik oprogramowania. **WinCounter** opcja musi być określona w wierszu polecenia, który zawiera **Start** opcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie ustawiono interwał próbkowania 1000 milisekund dla dwóch liczników wydajności systemu Windows.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)