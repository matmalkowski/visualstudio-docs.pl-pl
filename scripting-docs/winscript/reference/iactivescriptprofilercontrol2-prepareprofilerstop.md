---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Powiadamia profilera zamierza Zatrzymaj profilowanie na wszystkich odpowiednich aparatów skryptów. Za pomocą tej metody, można uzyskać stosu wywołań pełną, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] działa zatrzymanie profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Nie można uruchomić profilowania.|  
|`S_FALSE`|Profilowanie zostało zatrzymane, gdy skrypt nie został uruchomiony.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Nie włączono profilowanie.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie `IActiveScriptProfilerControl2::PrepareProfilerStop` zapewnia, że jest wysyłany zdarzeń dla funkcji w stosie wywołań. Ta metoda musi zostać wywołana przed zatrzymaniem profilowanie na aparat skryptów, który znajduje się na karcie bieżącego. Metodę można wywołać dla dowolnego aparatu skryptów.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Interfejs IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)