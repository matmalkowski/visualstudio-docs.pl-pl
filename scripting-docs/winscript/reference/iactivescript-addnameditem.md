---
title: IActiveScript::AddNamedItem | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db65361e4bde14e803d9085a4530a505ccaf9fcb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Dodaje nazwę elementu głównego poziomu do przestrzeni nazw aparatu skryptów. Element poziomu głównego jest obiekt o właściwości i metody, źródłem zdarzenia lub wszystkich trzech.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 [in] Adres buforu, który zawiera nazwę elementu, tak jak to pokazano w skrypcie. Nazwa musi być unikatowa i możliwy do utrwalenia.  
  
 `dwFlags`  
 [in] Flagi skojarzone z elementem. Może być kombinacją tych wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Wskazuje, czy nazwany element reprezentuje obiekt tylko kod i host nie ma `IUnknown` ma zostać skojarzony z tym obiektem tylko kod. Host zawiera tylko nazwę dla tego obiektu. Zorientowane obiektowo języków, takich jak C++ ta flaga utworzyć klasę. Nie obsługuje wszystkich języków tej flagi.|  
|SCRIPTITEM_GLOBALMEMBERS|Wskazuje, że element jest kolekcja globalnych właściwości i metod skojarzonych ze skryptem. Zwykle aparat skryptów rozróżnia nazwę obiektu (innych niż wyłącznie w celu używania go jako plik cookie dla [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) metody, lub w celu rozwiązania jawnego określania zakresu) i udostępnianie jej elementów członkowskich jako globalnego zmienne i metody. Umożliwia to hostowi rozszerzanie biblioteki (funkcje wykonawcze języka i tak dalej) dla skryptu. Zostanie pozostawiony do aparatu skryptów radzenia sobie z nazwa powoduje konflikt (na przykład, jeśli dwa elementy SCRIPTITEM_GLOBALMEMBERS mają metody o tej samej nazwie), chociaż nie powinien być zwracany błąd z powodu tej sytuacji.|  
|SCRIPTITEM_ISPERSISTENT|Wskazuje, czy element powinien być zapisany, zapisanie aparatu skryptów. Podobnie, ustawienie ta flaga wskazuje, że przejście do stanu zainicjowane powinien zachować elementu nazwę i typ informacji (aparat skryptów jednak wszystkie wskaźniki prowadzące do interfejsów rzeczywistego obiektu).|  
|SCRIPTITEM_ISSOURCE|Wskazuje, że element źródłem zdarzeń, które skrypt może sink. Obiekty podrzędne (właściwości obiektu znajdujących się w samych obiektów) można także źródła zdarzeń do skryptu. Nie jest cykliczne, ale na przykład zapewnia mechanizm wygodny w typowych przypadkach tworzenia kontenera i wszystkich jego elementów członkowskich kontrolki.|  
|SCRIPTITEM_ISVISIBLE|Wskazuje, że nazwa elementu jest dostępne w przestrzeni nazw skrypt umożliwiający dostęp do właściwości, metod i zdarzeń elementu. Konwencja właściwości elementu obejmują elementy podrzędne elementu; w związku z tym wszystkie właściwości obiektu podrzędnego i metody (i ich elementy podrzędne, rekursywnie) będą dostępne.|  
|SCRIPTITEM_NOCODE|Wskazuje, że element jest po prostu nazwę dodawane do skryptu obszar nazw i nie powinien być traktowany jako element, dla którego kod powinien być skojarzony. Na przykład bez ta flaga jest ustawiona, VBScript utworzy oddzielnego modułu o nazwie elementu i C++ może utworzyć klasy otoki osobne dla nazwanego elementu.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować).|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)