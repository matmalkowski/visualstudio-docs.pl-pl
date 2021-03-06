---
title: IActiveScriptAuthor::GetInfoFromContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3465552b99b2185ea475c5479f044ee7b27704ae
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281250"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Zwraca typu informacji i pozycji zakotwiczenia dla danego znaku w bloku kodu. Zawiera informacje dla elementu członkowskiego, IntelliSense, wykazy globalne i porady dotyczące parametru.  
  
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
 [in] Adres ciągu bloku kodu, które są używane do generowania wyników informacji.  
  
 `cchCode`  
 [in] Długość bloku kodu.  
  
 `ichCurrentPosition`  
 [in] Pozycja znaku względem początku bloku.  
  
 `dwListTypesRequested`  
 [in] Typy list żądanie. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Brak listy.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Lista elementów członkowskich.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Lista wyliczenia.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Wywołaj liście parametrów metody.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Globalna lista.|  
  
 Typ SCRIPT_CMPL_GLOBALLIST jest traktowany jako domyślny element ukończenia można łączyć za pomocą operatora OR z innymi elementami ukończenia. Skrypt tworzenia aparatu najpierw próbuje wypełnić informacji o typie dla inne listy uzupełniania. W przypadku niepowodzenia aparat wypełnienie dla SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 [out] Typ listy.  
  
 `pichListAnchorPosition`  
 [out] Indeks początkowy kontekst, który zawiera bieżącej pozycji. Indeks początkowy jest określana względem początku bloku.  
  
 To jest wypełniana tylko wtedy, gdy `dwListTypesRequested` obejmuje SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST lub SCRIPT_CMPL_GLOBALLIST. Dla innych typów żądanej listy wynik jest niezdefiniowany.  
  
 `pichFuncAnchorPosition`  
 [out] Indeks początkowy wywołania funkcji, która zawiera bieżące położenie. Indeks początkowy jest określana względem początku bloku.  
  
 To jest wypełniana tylko wtedy, gdy kontekst, który zawiera bieżące położenie jest wywołanie funkcji, a gdy `dwListTypesRequested` obejmuje SCRIPT_CMPL_PARAMLIST. W przeciwnym razie wynik jest niezdefiniowany.  
  
 `pmemid`  
 [out] MEMBERID funkcji, zgodnie z definicją według typu w `IProvideMultipleClassInfo``ppunk` parametr wyjściowy.  
  
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
 [Interfejs IProvideMultipleClassInfo](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [IActiveScriptAuthor, interfejs](../../winscript/reference/iactivescriptauthor-interface.md)