---
title: IActiveScriptAuthor::GetInfoFromContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27c13dbe51bb1150554275b5fbeacd00be2e445f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Zwraca typu informacji i pozycji zakotwiczenia dla danego znaku w bloku kodu. IntelliSense, wykazy globalne i porady parametru zapewnia informacje dla elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [in] Adres ciągu bloku kodu służącego do generowania wyników informacji.  
  
 `cchCode`  
 [in] Długość bloku kodu.  
  
 `ichCurrentPosition`  
 [in] Pozycja znaku względem początku bloku.  
  
 `dwListTypesRequested`  
 [in] Typy list żądanie. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Brak listy.|  
|SCRIPT_CMPL_MEMBERLIST|0X0001|Lista elementów członkowskich.|  
|SCRIPT_CMPL_ENUMLIST|0X0002|Lista wyliczenia.|  
|SCRIPT_CMPL_PARAMLIST|0X0004|Wywołanie metody listy parametrów.|  
|SCRIPT_CMPL_GLOBALLIST|0X0008|Globalna lista.|  
  
 Typ SCRIPT_CMPL_GLOBALLIST jest traktowany jako domyślny element ukończenia można łączyć przy użyciu operatora OR z innymi elementami ukończenia. Skrypt tworzenia aparatu najpierw próbuje wypełnić informacji o typie dla innych listy uzupełniania. W przypadku niepowodzenia aparat wypełnienie dla SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 [out] Typ listy.  
  
 `pichListAnchorPosition`  
 [out] Indeks początkowy kontekstu, która zawiera bieżące położenie. Indeks początkowy jest określana względem początku bloku.  
  
 To jest wypełniana tylko wtedy, gdy `dwListTypesRequested` obejmuje SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST lub SCRIPT_CMPL_GLOBALLIST. W przypadku innych typów Żądana lista wynik jest niezdefiniowany.  
  
 `pichFuncAnchorPosition`  
 [out] Indeks początkowy wywołania funkcji, która zawiera bieżące położenie. Indeks początkowy jest określana względem początku bloku.  
  
 To jest wypełniana tylko wtedy, gdy kontekstu, która zawiera bieżące położenie jest wywołanie funkcji, a gdy `dwListTypesRequested` obejmuje SCRIPT_CMPL_PARAMLIST. W przeciwnym razie wynikiem jest niezdefiniowany.  
  
 `pmemid`  
 [out] MEMBERID funkcji, zgodnie z definicją typu w `IProvideMultipleClassInfo``ppunk` parametr wyjściowy.  
  
 To jest wypełniana tylko wtedy, gdy `dwListTypesRequested` obejmuje SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 [out] Indeks parametru, która zawiera bieżące położenie. Jeśli bieżące położenie jest na nazwę funkcji, zwracana jest wartość -1.  
  
 `piCurrentParameter` Wartość jest wypełniana tylko wtedy, gdy `dwListTypesRequested` obejmuje SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Informacje o typie, który jest dostarczany w formie `IProvideMultipleClassInfo` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IProvideMultipleClassInfo](https://msdn.microsoft.com/library/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo.aspx)   
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)