---
title: IActiveScriptAuthor::GetLanguageFlags | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Zwraca informacje o języku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pgrfasa`  
 [out] Flagi, które zawierają informacje o języku. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0X0001|Język preferuje Tworzenie procedury obsługi zdarzeń skryptu za pomocą skryptu tworzenia aparatu, a nie aplikacji.|  
|fasaSupportInternalHandler|0X0002|Język obsługuje skryptu procedury obsługi zdarzeń utworzony przez skrypt tworzenia aparatu.|  
|fasaCaseSensitive|0X0004|Język skryptu jest uwzględniana wielkość liter.|  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli skrypt tworzenia aparatu zarządza procedury obsługi zdarzeń, aplikacji powinny wywoływać `CreateChildHandler` z `IScriptEntry` obiektu. Spowoduje to utworzenie `IScriptScriptlet` obiekt, który odpowiada programu obsługi zdarzeń. Aparat dodaje również program obsługi zdarzeń do wpisu skryptu. Procedura obsługi zdarzeń jest pusty funkcji, która zawiera informacje o określoną sygnaturą.  
  
 Jeśli aplikacja zarządza procedury obsługi zdarzeń, powinny wywoływać `CreateChildHandler` z `IScriptNode` obiekt, który reprezentuje skryptlet programu obsługi zdarzeń. Spowoduje to utworzenie `IScriptScriptlet` obiekt, który jest skojarzony z skryptlet programu obsługi zdarzeń. Aplikacja ma również dodać funkcję pusty jako zdarzenie program obsługi do nowego lub istniejącego `IScriptEntry` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)