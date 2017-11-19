---
title: IDispatchEx::InvokeEx | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Zapewnia dostęp do właściwości i metody ujawnione przez `IDispatchEx` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Określa element członkowski. Używa `GetDispID` lub `GetNextDispID` do uzyskania identyfikatora wysyłania.  
  
 `lcid`  
 Ustawienia regionalne kontekstu, w którym można interpretować argumenty. `lcid` Jest przekazywana do `InvokeEx` umożliwia obiektu interpretować argumenty specyficzne dla ustawień regionalnych.  
  
 `wFlags`  
 Wartości prawne `wFlags` są:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Flagi opisujące kontekście `InvokeEx` wywołania:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|DISPATCH_METHOD|Element członkowski jest wywoływany jako metody. Jeśli właściwość ma taką samą nazwę, można ustawić to i flagi DISPATCH_PROPERTYGET (zdefiniowane przez `IDispatch`).|  
|DISPATCH_PROPERTYGET|Element członkowski jest interpretowana jako właściwość lub danych elementu członkowskiego (zdefiniowane przez `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Element członkowski zostanie zmieniona jako element członkowski właściwości lub danych (zdefiniowane przez `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Element członkowski zostanie zmieniony przez przypisanie odwołania, a nie przypisanie wartości. Ta flaga jest prawidłowa tylko wtedy, gdy właściwość przyjmuje odwołanie do obiektu (zdefiniowane przez `IDispatch`).|  
|DISPATCH_CONSTRUCT|Element członkowski jest używany jako konstruktora. (Jest to nowa wartość zdefiniowana przez `IDispatchEx`). Wartości prawne `wFlags` są:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Wskaźnik do struktury zawiera tablicę argumentów, tablicę identyfikatorów DISPID argumentu dla nazwanych argumentów i zlicza liczbę elementów w tablicach. Zobacz `IDispatch` dokumentację, aby uzyskać pełny opis struktury DISPPARAMS.  
  
 `pVarRes`  
 Wskaźnik do lokalizacji, w którym wynik ma być przechowywanych lub wartość Null, jeśli element wywołujący oczekuje żadnego wyniku. Ten argument jest ignorowana, jeśli określono DISPATCH_PROPERTYPUT lub DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Wskaźnik do struktury, która zawiera informacje o wyjątku. Ta struktura powinno być wypełnione w przypadku `DISP_E_EXCEPTION` jest zwracany. Może mieć wartości Null. Zobacz `IDispatch` dokumentację, aby uzyskać pełny opis `EXCEPINFO` struktury.  
  
 `pspCaller`  
 Wskaźnik do obiektu dostawcy usługi dostarczony przez obiekt wywołujący, dzięki czemu obiekt do uzyskania usług wywołujący. Może mieć wartości Null.  
  
 `IDispatchEx::InvokeEx`udostępnia wszystkie te same funkcje co `IDispatch::Invoke` i dodaje kilka rozszerzeń:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Wskazuje, czy element jest używany jako konstruktora.|  
|`pspCaller`|`pspCaller` Umożliwia uzyskanie obiektu dostępu do usług świadczonych przez obiekt wywołujący. Określonych usług mogą być obsługiwane przez sam obiekt wywołujący lub delegowane do wywoływania dalsze zapasowej łańcuch wywołań. Na przykład, jeśli aparat skryptów w przeglądarce sprawia, że `InvokeEx` wykonać wywołania obiektu zewnętrznego obiektu `pspCaller` łańcucha uzyskania usług z aparatu skryptu lub przeglądarki. (Należy pamiętać, że łańcuch wywołań nie jest taka sama jak tworzenie łańcucha — znanej także jako kontener łańcucha lub łańcuch lokacji. Tworzenie łańcucha mogą być dostępne innym mechanizmem takich jak `IObjectWithSite`.)|  
|`this`wskaźnik|Jeśli DISPATCH_METHOD jest ustawiona w `wFlags`, może być "parametr o nazwie" wartość "this". Identyfikator DISPID będzie DISPID_THIS i musi być pierwszym parametrem nazwanego.|  
  
 Nieużywane `riid` parametru w `IDispatch::Invoke` został usunięty.  
  
 `puArgArr` Parametru w `IDispatch::Invoke` został usunięty.  
  
 Zobacz `IDispatch::Invoke` dokumentacji następujące przykłady:  
  
 "Podczas wywoływania metody bez argumentów"  
  
 "Pobieranie i ustawianie właściwości"  
  
 "Przekazywanie parametrów"  
  
 "Właściwości indeksowanej"  
  
 "Występowanie wyjątków podczas wywołania"  
  
 "Zwraca błędy"  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|DISP_E_BADPARAMCOUNT|Liczba elementów do DISPPARAMS różni się od liczby argumentów akceptowanych przez metody lub właściwości.|  
|DISP_E_BADVARTYPE|Jeden z argumentów `rgvarg` nie jest prawidłowym typem variant.|  
|DISP_E_EXCEPTION|Aplikacja musi wygenerować wyjątek. W takim przypadku struktury przekazano `pei` powinno być wypełnione.|  
|DISP_E_MEMBERNOTFOUND|Żądany element nie istnieje, lub wywołanie `InvokeEx` próbowano ustawić wartość właściwości tylko do odczytu.|  
|DISP_E_NONAMEDARGS|Ta implementacja `IDispatch` nie obsługuje argumentów nazwanych.|  
|DISP_E_OVERFLOW|Jeden z argumentów `rgvarg` nie można przekształcić do określonego typu.|  
|DISP_E_PARAMNOTFOUND|Jeden z parametrów identyfikator DISPID jest niezgodne z parametrem w metodzie.|  
|DISP_E_TYPEMISMATCH|Nie można rzutować co najmniej jeden z argumentów.|  
|DISP_E_UNKNOWNLCID|Zinterpretował argumenty ciągu zgodnie z LCID, i identyfikator LCID nie został rozpoznany. Jeśli identyfikator LCID nie jest potrzebny do interpretowania argumenty, ten błąd nie powinien być zwracany.|  
|DISP_E_PARAMNOTOPTIONAL|Wymagany parametr został pominięty.|  
  
## <a name="example"></a>Przykład  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)