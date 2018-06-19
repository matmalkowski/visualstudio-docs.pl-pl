---
title: IActiveScriptProperty::GetProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793969"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Pobiera właściwość, która jest określona przez parametr.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwProperty`  
 Wartości właściwości do pobrania.  
  
 `pvarIndex`  
 Nie używany.  
  
 `pvarValue`  
 Wartość właściwości.  
  
 Dozwolone wartości dla `dwProperty` są opisane w poniższej tabeli.  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Wymusza aparat skryptów do dzielenia w trybie całkowitą zamiast przestawne trybie punktu.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Umożliwia funkcji Porównaj ciąg aparat skryptów, które mają zostać zastąpione.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informuje o aparatów skryptów, który istnieje innych aparatów skryptów przyczynić się do obiektu globalnego.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Wymusza [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat skryptów, aby wybrać zestaw funkcji języka aby można było obsługiwać. Domyślny zestaw funkcji językowych obsługiwanych przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat skryptów jest odpowiednikiem języka zestaw funkcji, które znajdowały się w wersji 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparatu skryptów.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument jest nieprawidłowy.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować).|  
  
## <a name="remarks"></a>Uwagi  
 Hosta można użyć właściwości SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION informują o tym aparatów skryptów, który istnieje innych aparatów skryptów przyczynić się do obiektu globalnego. Na przykład program Internet Explorer można poinformować [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparatu, zawierający tylko renderowanej strony [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skryptów. W związku z tym tylko [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat można dodać nowych właściwości do okna obiekt globalny i nie żaden aparat Visual Basic Scripting Edition (VBScript) na tym samym. Aparat można zignorować tę flagę lub służy do optymalizacji zarządzania nowych elementów członkowskich, które są dodawane do globalnego obiektu.  
  
 Hosta można użyć właściwości SCRIPTPROP_INVOKEVERSIONING wybierz zestaw funkcji języka aby być obsługiwane w przypadku [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat skryptów jest uruchomiona. Jeśli ta właściwość jest ustawiona na wartość 1 (SCRIPTLANGUAGEVERSION_5_7), funkcje językowe dostępne są takie same jak te, które znajdowały się w wersji 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparatu skryptów. Jeśli ustawiono 2 (SCRIPTLANGUAGEVERSION_5_8), funkcje językowe dostępne są te, które znajdowały się w wersji 5.7 Oprócz funkcji, które zostały dodane w wersji 5.8. Domyślnie ta właściwość jest równa 0 (SCRIPTLANGUAGEVERSION_DEFAULT), który jest odpowiednikiem języka zestaw funkcji, które znajdowały się w wersji 5.7, chyba że host obsługuje różne domyślne zachowanie. Na przykład wybranych programu Internet Explorer 8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcje językowe obsługiwane przez wersję 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat skryptów domyślnie, gdy tryb dokumentu dla programu Internet Explorer 8 jest tryb "Standardów programu Internet Explorer 8".  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie zgodności dokumentów](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informacje o wersji](../../javascript/reference/javascript-version-information.md)