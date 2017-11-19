---
title: IActiveScript::GetScriptSite | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 961483d45c72018bc216306d6c1aba0400a367ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Pobiera obiekt lokacji skojarzonego z aparatem skryptów systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator żądanego interfejsu.  
  
 `ppvSiteObject`  
 [out] Adres lokalizacji, która odbiera wskaźnika interfejsu do obiektu witryny hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_NOINTERFACE`|Określony interfejs nie jest obsługiwany.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`S_FALSE`|Lokacja nie została ustawiona; `ppvSiteObject` ustawiono parametr `NULL`.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)