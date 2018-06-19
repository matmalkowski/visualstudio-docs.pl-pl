---
title: IDebugHelper::CreatePropertyBrowserEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9bc219ea5c2ff9ff2860d36cd475985d825ae59
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794425"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Zwraca przeglądarki właściwość, która opakowuje wariant i umożliwia konwersji niestandardowej wartości z WARIANTU lub typów VARTYPE na ciągi.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvar`  
 [in] Wariant głównego do przeglądania.  
  
 `bstrName`  
 [in] Nazwa katalogu głównego.  
  
 `pdat`  
 [in] Wątek, na których chcesz żądać właściwości. Jeśli ten parametr ma wartość NULL, kierowanie nie jest wykonywana.  
  
 `pdf`  
 [in] Obiekt, który zawiera niestandardowe formatowanie wariantów.  
  
 `ppdob`  
 [out] Przeglądarka właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca przeglądarki właściwość, która opakowuje wariant i umożliwia konwersji niestandardowej wartości z WARIANTU lub typów VARTYPE na ciągi.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Interfejs IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)