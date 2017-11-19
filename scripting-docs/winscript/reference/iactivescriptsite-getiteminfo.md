---
title: IActiveScriptSite::GetItemInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Umożliwia aparat skryptów uzyskać informacje o elemencie dodane z [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 [in] Nazwa skojarzona z elementem, jak określono w [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metody.  
  
 `dwReturnMask`  
 [in] Maska bitowa określania, jakie informacje o elemencie ma zostać zwrócony. Aparat skryptów powinien zażądać minimalną ilość informacji możliwe, ponieważ niektóre z parametrów zwracanych (na przykład `ITypeInfo`) może zająć wiele czasu ładowania lub wygenerować. Może być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Zwraca `IUnknown` interfejs dla tego elementu.|  
|SCRIPTINFO_ITYPEINFO|Zwraca `ITypeInfo` interfejs dla tego elementu.|  
  
 `ppunkItem`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IUnknown` skojarzone z danym elementem interfejsu. Można używać aparatu skryptów `IUnknown::QueryInterface` metodę, aby uzyskać `IDispatch` interfejs dla elementu. Ten parametr odbiera wartość NULL, jeśli `dwReturnMask` nie ma wartości SCRIPTINFO_IUNKNOWN. Ponadto odbiera wartość NULL, jeśli nie ma żadnego obiektu skojarzone z nazwą elementu; Mechanizm ten jest używany do tworzenia prostą klasę, gdy nazwany element został dodany przy użyciu flagi SCRIPTITEM_CODEONLY w [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metody.  
  
 `ppTypeInfo`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `ITypeInfo` skojarzone z elementem interfejsu. Ten parametr odbiera wartość NULL, jeśli `dwReturnMask` nie ma wartości SCRIPTINFO_ITYPEINFO lub jeśli informacje o typie nie jest dostępna dla tego elementu. Jeśli nie ma informacji o typie obiektu nie źródła zdarzeń i powiązania nazwy musi być realizowany z `IDispatch::GetIDsOfNames` metody. Należy pamiętać, że `ITypeInfo` interfejsu pobrać opisuje coclass elementu (TKIND_COCLASS), ponieważ obiekt może obsługiwać wiele interfejsów i interfejsów zdarzeń. Jeśli element obsługuje `IProvideMultipleTypeInfo` interfejsu `ITypeInfo` interfejsu pobierana jest taka sama jak indeksie zero `ITypeInfo` który będzie można uzyskać przy użyciu `IProvideMultipleTypeInfo::GetInfoOfIndex` — metoda.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`TYPE_E_ELEMENTNOTFOUND`|Nie znaleziono elementu o podanej nazwie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera tylko te informacje, które określają `dwReturnMask` parametru; poprawia to wydajność. Na przykład jeśli `ITypeInfo` interfejsu nie jest wymagany dla elementu, po prostu nie został określony w `dwReturnMask`.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)