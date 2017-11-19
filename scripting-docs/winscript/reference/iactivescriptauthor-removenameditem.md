---
title: IActiveScriptAuthor::RemoveNamedItem | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.RemoveNamedItem
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f3acc7d61d63ce4fb4fe53729ce43324b9718a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Usuwa `NamedItem` obiektu z przestrzeni nazw, tworzenia aparatu skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [in] Adres buforu, który identyfikuje `NamedItem` obiekt ma zostać usunięty.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`S_FALSE`|`NamedItem` Obiekt nie znajduje się w przestrzeni nazw, tworzenia aparatu skryptu.|  
  
## <a name="remarks"></a>Uwagi  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) służy do dodania `NamedItem` obiekt do tworzenia nazw aparatu skryptu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)