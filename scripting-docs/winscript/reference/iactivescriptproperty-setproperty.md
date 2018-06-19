---
title: IActiveScriptProperty::SetProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc9b5f4c0d02789988bb41f46417651414beed7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794104"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Ustawia właściwość, która jest określona przez parametr.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetProperty(  
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
 Wartość właściwości do ustawienia.  
  
 `pvarIndex`  
 Nie używany.  
  
 `pvarValue`  
 Wartość właściwości.  
  
 Dozwolone wartości dla `dwProperty` są opisane w poniższej tabeli.  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Wymusza aparat skryptów do dzielenia w trybie całkowitą zamiast przestawne trybie punktu. Wartość domyślna to `False`.|  
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
 Aby włączyć lub wyłączyć dzielenie liczby całkowitej, wywołaj `SetProperty` i przekonwertować `Boolean` do `Object`. Domyślnie wartość właściwości jest `False`. Jeśli zostanie ustawiona `True`, zwraca tylko liczby całkowite z operacji dzielenia.  
  
 Aby włączyć lub wyłączyć porównania niestandardowy ciąg, wywołaj `SetProperty` i podaj `Object` wartość. Obiekt, który jest przekazywane w musi implementować interfejs [interfejs IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md). [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) metody [interfejs IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) interfejsu jest nazywany zawsze Funkcja porównywania ciągów jest wykonywana.  
  
 Aby wybrać zestaw funkcji języka Aby obsługiwane, gdy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] zainicjowano aparatu skryptów, wywołaj `SetProperty` i przekaż wartość, która odnosi się do zestawu być włączone dla SCRIPTPROP_INVOKEVERSIONING funkcji języka. Jeśli ta właściwość jest ustawiona na wartość 1 (SCRIPTLANGUAGEVERSION_5_7), funkcje językowe dostępne są takie same jak te, które znajdowały się w wersji 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparatu skryptów. Jeśli ustawiono 2 (SCRIPTLANGUAGEVERSION_5_8), funkcje językowe dostępne są te, które znajdowały się w wersji 5.7 Oprócz nowych funkcji, które zostały dodane w wersji 5.8. Domyślnie ta właściwość jest równa 0 (SCRIPTLANGUAGEVERSION_DEFAULT), który jest odpowiednikiem języka zestaw funkcji, które znajdowały się w wersji 5.7, chyba że host obsługuje różne domyślne zachowanie. Na przykład programu Internet Explorer 8 wybranych [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcje językowe, które są obsługiwane przez wersję 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat skryptów domyślnie, gdy domyślny tryb dokumentu dla programu Internet Explorer 8 jest tryb "Standardów programu Internet Explorer 8". Przełączanie trybu dokumentów programu Internet Explorer 8 do standardów programu Internet Explorer 7 lub Osobliwości resetuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat skryptów do obsługi tylko zestaw funkcji językowych które istniały w wersji 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparatu skryptów.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING powinna być ustawiona tylko wtedy, gdy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] zainicjowano aparatu skryptów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wymusić aparat skryptów umożliwia dzielenie liczby całkowitej i umożliwić przeciążanie funkcji Porównaj.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie zgodności dokumentów](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informacje o wersji](../../javascript/reference/javascript-version-information.md)