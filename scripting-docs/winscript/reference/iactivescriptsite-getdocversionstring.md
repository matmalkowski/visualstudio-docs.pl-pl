---
title: IActiveScriptSite::GetDocVersionString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Pobiera ciąg zdefiniowany przez hosta, który unikatowo identyfikuje bieżącej wersji dokumentu. Jeśli powiązanego dokumentu został zmieniony poza zakresem skryptu systemu Windows (tak jak w przypadku edycji w Notatniku strony HTML), aparat skryptów można zapisać to wraz z jego stanu utrwalonego wymuszanie ponownego kompilowania przy następnym załadowaniu skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrVersionString`  
 [out] Adres ciąg wersji dokumentu zdefiniowanego przez hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_NOTIMPL` Jeśli ta metoda nie jest obsługiwana.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `E_NOTIMPL` jest zwracany, aparat skryptów należy zakładać, że skrypt jest zsynchronizowana z dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)