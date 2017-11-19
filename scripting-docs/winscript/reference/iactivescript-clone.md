---
title: IActiveScript::Clone | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Klonów bieżącego aparatu skryptów (minus wszelkie bieżący stan wykonania), zwracając załadować aparatów skryptów, który ma żadna lokacja w bieżącym wątku. Właściwości to nowy aparat skryptów będą takie same jak właściwości, które oryginalny aparat skryptu byłoby w, jeśli zostały są przenoszone do stanu zainicjowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppscript`  
 [out] Adres zmiennej, która otrzymuje wskaźnik [IActiveScript](../../winscript/reference/iactivescript.md) interfejsu sklonowany aparatu skryptów. Host musi utworzyć witryny i wywołanie [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) metody na nowy aparat skryptu, zanim będzie on w stanie zainicjowania i w związku z tym można używać.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować).|  
  
## <a name="remarks"></a>Uwagi  
 `IActiveScript::Clone` Metoda jest optymalizacji `IPersist*::Save`, `CoCreateInstance`, i `IPersist*::Load`, więc stan aparat skryptów powinny być takie same, jakby stan oryginalny aparat skryptu zostały zapisane i ładowane do nowy aparat skryptów. Nazwanych elementów są duplikowane w sklonowanej aparatu skryptów, ale wskaźniki konkretny obiekt dla każdego elementu są zapomnienia hasła i są pobierane z [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) metody. Dzięki temu model obiektowy identyczne z punktami dostępu dla każdego wątku (modelu typu apartment) do użycia.  
  
 Ta metoda jest używana dla hostów serwera wielowątkowe, które można uruchomić wiele wystąpień tego samego skryptu. Aparat skryptów może zwrócić `E_NOTIMPL`, w którym to przypadku hosta można osiągnąć ten sam rezultat duplikowania trwały stan i tworzenie nowego wystąpienia aparatu skryptów z `IPersist*` interfejsu.  
  
 Ta metoda może być wywołana z wątków innych niż podstawowe powodowała objaśnienia innych niż podstawowe do obiektów hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)