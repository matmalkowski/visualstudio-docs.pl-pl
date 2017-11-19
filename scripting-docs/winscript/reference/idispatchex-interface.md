---
title: Interfejs IDispatchEx | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a100a193f5e3abcb076fb8aaf3d64a0d0c38833
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchex-interface"></a>Interfejs IDispatchEx
`IDispatchEx`, rozszerzenie `IDispatch` interfejsu, obsługuje funkcje właściwe w przypadku dynamicznego języków, takich jak języki skryptów. W tej sekcji opisano `IDispatchEx` interfejsu, różnice między `IDispatch` i `IDispatchEx`oraz uzasadnienie rozszerzeń. Oczekuje się, że czytników zna `IDispatch` i mają dostęp do `IDispatch` dokumentacji.  
  
## <a name="remarks"></a>Uwagi  
 `IDispatch`został opracowany zasadniczo dla programu Microsoft Visual Basic. Ograniczenia podstawowe `IDispatch` jest przyjęto założenie, że obiekty są statyczne. Innymi słowy ponieważ obiekty nie należy zmieniać w czasie wykonywania, informacje o typie można całkowicie opisano je w czasie kompilacji. Dynamiczne modeli środowiska wykonawczego, które znajdują się w językach skryptów, takich jak Visual Basic Scripting Edition (VBScript) i [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] i obiektu modeli, takie jak bardziej elastyczne interfejsu wymagają DHTML.  
  
 `IDispatchEx`został opracowany, aby zapewnić wszystkich usług `IDispatch` oraz niektóre rozszerzenia, które są odpowiednie dla bardziej dynamiczne języków późnym wiązaniem, takich jak języki skryptów. Dodatkowe funkcje `IDispatchEx` innych niż te dostarczone przez `IDispatch` są:  
  
-   Dodawanie nowych elementów członkowskich do obiektu ("expando") — użyj `GetDispID` z `fdexNameEnsure` flagi.  
  
-   Usuwanie elementów członkowskich obiektu — użyj `DeleteMemberByName` lub `DeleteMemberByDispID`.  
  
-   Operacje wysyłania z uwzględnieniem wielkości liter — użyj `fdexNameCaseSensitive` lub `fdexNameCaseInsensitive`.  
  
-   Wyszukaj element członkowski o nazwie niejawne — użyj `fdexNameImplicit`.  
  
-   Wyliczanie identyfikator DISPID obiektu — użyj `GetNextDispID`.  
  
-   Mapowanie nazwy elementu z identyfikatorem DISPID — użyj `GetMemberName`.  
  
-   Uzyskaj właściwości elementów członkowskich obiektu — użyj `GetMemberProperties`.  
  
-   Wywołanie metody z `this` wskaźnika — użyj `InvokeEx` z DISPATCH_METHOD.  
  
-   Zezwalaj na przeglądarek, które obsługują pojęcie przestrzenie nazw, aby uzyskać obiekt nadrzędny przestrzeni nazw — użyj `GetNameSpaceParent`.  
  
 Obiekty obsługujące `IDispatchEx` mogą także obsługiwać `IDispatch` zgodności z poprzednimi wersjami. Dynamiczne rodzaj obiektów, które obsługują `IDispatchEx` ma kilka wpływ na `IDispatch` interfejsu tych obiektów. Na przykład `IDispatch` założeń następujące:  
  
-   Element członkowski i parametr identyfikator DISPID musi pozostać stałej dla okresu istnienia obiektu. Dzięki temu klient może uzyskać identyfikator DISPID raz i buforowania ich do późniejszego użycia.  
  
 Ponieważ `IDispatchEx` umożliwia dodawanie i usuwanie elementów członkowskich, zbiór prawidłowy identyfikator DISPID nie pozostaje stała. Jednak `IDispatchEx` wymaga stałej pozostawienie mapowanie między nazwa DISPID i element członkowski. Oznacza to, że jeśli element członkowski zostanie usunięty:  
  
-   Nie można użyć ponownie identyfikator DISPID, dopóki nie zostanie utworzony element członkowski o takiej samej nazwie.  
  
-   Identyfikator DISPID musi pozostać dotyczy `GetNextDispID`.  
  
-   Identyfikator DISPID musi być bezpiecznie zaakceptowana przez żaden z `IDispatch` lub `IDispatchEx` metody — musi rozpoznać element członkowski jako usunięty i zwracają kod błędu odpowiednie (zazwyczaj DISP_E_MEMBERNOTFOUND lub wartości S_FALSE).  
  
## <a name="examples"></a>Przykłady  
 To [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kod w test() funkcja wykonuje następujące czynności:  
  
-   Tworzy nowy obiekt przez wywołanie metody `Object` Konstruktor i przypisuje wskaźnik do nowego obiektu do zmiennej obiektu  
  
-   Tworzy nowy element o nazwie elementu w obiekcie, a następnie przypisuje do tego elementu wskaźnika do funkcji cat.  
  
-   Wywołanie tej funkcji. Ponieważ jest ona wywoływana jako metody, `this` wskaźnika odwołuje się do obiektu obiektu Funkcja dodaje nowy element, pasek do obiektu.  
  
 Pełny kod HTML jest:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Formantu znajdującego się na tej samej stronie sieci Web można uzyskać wskaźnik wysyłania do aparatów skryptów w przeglądarce. Kontrolki można następnie wdrożyć to rozwiązanie test() funkcji:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Kod z formantu, testowanie i jest odpowiednikiem [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcja `test()`. Należy pamiętać, że te wysyłania wywołań do uruchamiania [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat i Zmień stan aparatu:  
  
-   Uzyskuje wskaźnik wysyłania przy użyciu funkcji cat `GetDispID()`.  
  
-   Uzyskuje wskaźnik wysyłania przy użyciu funkcji obiektu `GetDispID()`.  
  
-   Tworzy obiekt przez wywołanie funkcji z obiektu `InvokeEx()` i uzyskuje wskaźnik wysyłania do nowo skonstruowanego obiektu.  
  
-   Tworzy nowy element, element, za pomocą obiektu `GetDispID()` z `fdexNameEnsure` flagi.  
  
-   Umieszcza kursor wysyłania do cat za pomocą elementu `InvokeEx()`.  
  
-   Wywołuje wskaźnik wysyłania do cat jako metoda wywołując `InvokeEx()` i przekazanie wskaźnika wysyłania do skonstruowanego obiektu jako `this` wskaźnika.  
  
-   Metoda cat tworzy nowy element paska w bieżącej `this` obiektu.  
  
-   Sprawdza, czy nowy element paska, został utworzony w obiekcie utworzone przez wyliczania elementów za pomocą `GetNextDispID()`.  
  
 Kod dla formantu testu:  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Metody  
 [Metody IDispatchEx](../../winscript/reference/idispatchex-methods.md)