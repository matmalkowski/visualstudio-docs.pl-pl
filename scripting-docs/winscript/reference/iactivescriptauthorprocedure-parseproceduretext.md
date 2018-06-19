---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9c4a1ba03a8498dbaa857dc5dbabba8914e54a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793285"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analizuje procedury kodu, dodaje tekst procedury kodu do skryptu tworzenia aparatu i tworzy `IScriptEntry` obiekt, który odpowiada procedury kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [in] Tekst skryptu, można przeanalizować.  
  
 `pszFormalParams`  
 [in] Adres nazwy formalny parametr dla procedury. Nazwy parametrów muszą być oddzielone odpowiednie ograniczniki dla tworzenia aparatu skryptu. Nazwy nie powinny być ujęte w nawiasy.  
  
 `pszProcedureName`  
 [in] Adres nazwę procedury do przeanalizowania.  
  
 `pszItemName`  
 [in] Adres buforu, który zawiera nazwę elementu skojarzone z `IScriptEntry` obiektu.  
  
 `pszDelimiter`  
 [in] Adres ogranicznik zakończenia elementu skryptu bloku. Gdy `pszCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik (na przykład dwa pojedynczy cudzysłów), aby wykryć koniec bloku skryptu. Ustaw ten parametr na wartość NULL, jeśli nie istnieje żadne ogranicznik można oznaczyć końca bloku skryptu.  
  
 `dwCookie`  
 [in] Zdefiniowane przez aplikację wartość skojarzoną z nowym `IScriptEntry` obiektu.  
  
 `dwFlags`  
 [in] Nie jest używany.  
  
 `pdispFor`  
 [in] Nie jest używany.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Bieżący [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat nie obsługuje tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)