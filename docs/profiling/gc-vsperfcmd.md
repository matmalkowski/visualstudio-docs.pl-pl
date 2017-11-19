---
title: GC (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da671dcac0e60c0d20754d73f9b23a9fe2de54d5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
**GC** opcja umożliwia zbieranie danych .NET Framework pamięci alokacji i obiektu okres istnienia. **GC** opcja może być używana tylko z metoda profilowania próbkowania i tylko **uruchamianie** opcji.  
  
 W przypadku używania **GC** opcję VSPerfClrEnv **/sampleon** polecenia nie jest wymagana.  
  
 Jeśli nie określono żadnych parametrów lub **alokacji** parametr jest określony, są zbierane tylko .NET Framework danych alokacji pamięci. Jeśli **okres istnienia** parametr jest określony, alokacji pamięci .NET Framework i .NET Framework obiekt zbieranych danych o okresie istnienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 **Alokacja**  
 Domyślne. Zbiera dane alokacji pamięci .NET Framework.  
  
 **Cykl życia**  
 Zbiera dane, zarówno dane alokacji pamięci .NET Framework i danych o okresie istnienia obiektu platformy .NET Framework.  
  
## <a name="required-options"></a>Wymagane opcje  
 **GC** opcja może być używana tylko z **uruchamianie** opcji.  
  
 **Uruchom:**`AppName`  
 Uruchamia określony aplikację i rozpocznie się profilowania za pomocą metody pobierania próbek.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie uruchamia aplikację i zbiera dane alokacji pamięci .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)