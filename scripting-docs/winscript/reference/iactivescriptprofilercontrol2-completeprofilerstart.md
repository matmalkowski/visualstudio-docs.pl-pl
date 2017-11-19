---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Powiadamia profilera rozpoczęto profilowanie na wszystkich odpowiednich aparatów skryptów. Za pomocą tej metody, można uzyskać stosu wywołań pełną, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] działa podczas uruchamiania profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Nie można uruchomić profilowania.|  
|`S_FALSE`|Profilowanie uruchomienia skryptu nie zostało uruchomione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Nie włączono profilowanie. Bez wywołania zwrotnego został ustawiony.|  
|`E_OUTOFMEMORY`|Stos wywołań nie można uzyskać z powodu braku pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie `IActiveScriptProfilerControl2::CompleteProfilerStart` zapewnia, że jest wysyłany zdarzeń dla funkcji w stosie wywołań. Ta metoda ma być wywoływany po profilowaniu rozpoczyna się na aparat skryptów, który znajduje się na karcie bieżącego. Metodę można wywołać dla dowolnego aparatu skryptów.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Interfejs IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)