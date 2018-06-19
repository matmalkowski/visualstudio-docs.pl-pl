---
title: IDebugDocumentHelper::DefineScriptBlock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794254"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Wskazuje do elementu pomocniczego do określonego zakresu znaków blok skryptu, który jest obsługiwany przez aparat skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ulCharOffset`  
 [in] Lokalizacja początku bloku skryptu.  
  
 `cChars`  
 [in] Liczba znaków w bloku skryptu.  
  
 `pas`  
 [in] Aparat skryptów dla tego bloku skryptu.  
  
 `fScriptlet`  
 [in] Flaga, która wskazuje, czy blok skryptu jest skryptlet.  
  
 `pdwSourceContext`  
 [out] Kontekst źródła dla bloku skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Host inteligentny można użyć tej metody, podczas jego dokumenty zawierają bloki osadzony skrypt. Aparat języka można użyć tej metody, jeśli jego kod zawiera osadzonych skryptów dla innych języków.  
  
 Aparat skryptu jest odpowiedzialny za wszystkie składni kolorowanie i kod kontekstu wyszukiwania w bloku skryptu.  
  
 `DefineScriptBlock` Metoda powinna być wywoływana po dodaniu tekst (na przykład za pomocą `IDebugDocumentHelper::AddDBCSText` metodę), ale przed skrypt przeanalizowaniu bloku (na przykład za pomocą `IActiveScriptParse ::ParseScriptText` — metoda).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)