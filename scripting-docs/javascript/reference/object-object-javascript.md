---
title: "Object — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- object
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Object object
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e82b9c66c286c7f847e7b67b1b5928aadd613e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="object-object-javascript"></a>Object — Obiekt (JavaScript)
Udostępnia funkcje wspólne dla wszystkich [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
obj  
 = new Object([value])   
```  
  
## <a name="parameters"></a>Parametry  
 `obj`  
 Wymagany. Nazwa zmiennej, do której `Object` obiekt jest przypisany.  
  
 *wartość*  
 Opcjonalny. Jeden z [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] typy pierwotne danych (liczba, Boolean lub String). Jeśli wartość jest obiektu, obiekt jest zwracany bez modyfikacji. Jeśli *wartość* jest `null`, **Niezdefiniowany**, lub nie został podany, jest tworzony obiekt z żadnej zawartości.  
  
## <a name="remarks"></a>Uwagi  
 `Object` Obiekt znajduje się w pozostałych [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektów; wszystkie metody i właściwości są dostępne w innych obiektów. Metody można ponownie zdefiniować w obiekty zdefiniowane przez użytkownika i są wywoływane przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] w odpowiednim czasie. **ToString** metoda jest przykładem często zmieniony `Object` metody.  
  
 W niniejszej dokumentacji języka opis każdego `Object` metoda zawiera domyślnych i uzyskać informacje o wewnętrznej implementacji określonego obiektu [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektów.  
  
## <a name="requirements"></a>Wymagania  
 `Object Object` Została wprowadzona w systemie [!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)]. Niektóre elementy członkowskie wymienione na poniższej liście zostały wprowadzone w nowszych wersjach.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `Object Object`.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[__proto\_ \_ właściwości](../../javascript/reference/proto-property-object-javascript.md)|Określa prototypu dla obiekt.|  
|[constructor — właściwość](../../javascript/reference/constructor-property-object-javascript.md)|Określa funkcję, która tworzy obiekt.|  
|[prototype — właściwość](../../javascript/reference/prototype-property-object-javascript.md)|Zwraca odwołanie do prototypu klasy obiektów.|  
  
## <a name="functions"></a>Funkcje  
 W poniższej tabeli wymieniono funkcje `Object Object`.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[Object.Assign — funkcja](../../javascript/reference/object-assign-function-object-javascript.md)|Kopiuje wartości z jednego lub większej liczby obiektów źródła do obiektu docelowego.|  
|[Object.Create — funkcja](../../javascript/reference/object-create-function-javascript.md)|Tworzy obiekt mający określonego prototypu i opcjonalnie zawiera określonej właściwości.|  
|[Object.defineproperties — funkcja](../../javascript/reference/object-defineproperties-function-javascript.md)|Dodaje jedną lub więcej właściwości do obiektu i/lub modyfikuje atrybuty istniejącej właściwości.|  
|[Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md)|Dodaje właściwość do obiektu lub zmienia atrybuty istniejącej właściwości.|  
|[Object.FREEZE — funkcja](../../javascript/reference/object-freeze-function-javascript.md)|Modyfikację istniejące atrybuty właściwości i wartości i uniemożliwia dodanie nowych właściwości.|  
|[Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|Zwraca definicji właściwości danych lub właściwości metody dostępu.|  
|[Object.getownpropertynames — funkcja](../../javascript/reference/object-getownpropertynames-function-javascript.md)|Zwraca nazwy właściwości i metod obiektu.|  
|[Object.getownpropertysymbols — funkcja](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|Zwraca symbol właściwości obiektu.|  
|[Object.getprototypeof — funkcja](../../javascript/reference/object-getprototypeof-function-javascript.md)|Zwraca prototypu obiektu.|  
|[Object.is — funkcja](../../javascript/reference/object-is-function-javascript.md)|Zwraca wartość wskazującą, czy dwie wartości są identyczne.|  
|[Object.isextensible — funkcja](../../javascript/reference/object-isextensible-function-javascript.md)|Zwraca wartość wskazującą, czy można dodawać nowych właściwości do obiektu.|  
|[Object.isfrozen — funkcja](../../javascript/reference/object-isfrozen-function-javascript.md)|Zwraca `true` Jeśli istniejące atrybuty właściwości i wartości nie można zmodyfikować obiektu i nie można dodać nowych właściwości do obiektu.|  
|[Object.issealed — funkcja](../../javascript/reference/object-issealed-function-javascript.md)|Zwraca `true` Jeśli istniejące atrybuty właściwości nie można zmodyfikować obiektu i nie można dodać nowych właściwości do obiektu.|  
|[Object.keys — funkcja](../../javascript/reference/object-keys-function-javascript.md)|Zwraca nazwy wyliczenia właściwości i metod obiektu.|  
|[Object.preventextensions — funkcja](../../javascript/reference/object-preventextensions-function-javascript.md)|Uniemożliwia dodanie nowych właściwości do obiektu.|  
|[Object.Seal — funkcja](../../javascript/reference/object-seal-function-javascript.md)|Modyfikację atrybuty istniejącej właściwości i uniemożliwia dodanie nowych właściwości.|  
|[Funkcja Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)|Ustawia prototypu obiektu.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Object Object`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[hasOwnProperty — metoda](../../javascript/reference/hasownproperty-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy obiekt ma właściwość o określonej nazwie.|  
|[isPrototypeOf — metoda](../../javascript/reference/isprototypeof-method-object-javascript.md)|Zwraca wartość logiczną, wskazującą, czy obiekt istnieje w hierarchii prototypu innego obiektu.|  
|[propertyIsEnumerable — metoda](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy określona właściwość jest częścią obiektu i czy jest wyliczalna.|  
|[toLocaleString — metoda](../../javascript/reference/tolocalestring-method-object-javascript.md)|Zwraca obiekt konwertowana na ciąg w oparciu o bieżące ustawienia regionalne.|  
|[toString — metoda](../../javascript/reference/tostring-method-object-javascript.md)|Zwraca reprezentację ciągu obiektu.|  
|[valueOf — metoda](../../javascript/reference/valueof-method-object-javascript.md)|Zwraca wartość pierwotnych określonego obiektu.|  
  
## <a name="see-also"></a>Zobacz też  
 [JavaScript — obiekty](../../javascript/reference/javascript-objects.md)