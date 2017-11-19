---
title: IActiveScriptAuthor::AddNamedItem | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83d2597f8468bb97d20da655a56a751191ec4b55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Dodaje nazwę elementu głównego poziomu do skryptu tworzenia aparatu przestrzeni nazw. A *elementu poziomu głównego* jest obiektem, który może zawierać właściwości i metody, a zawierających można również źródłem zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [in] Nazwa elementu, tak jak to pokazano w skrypcie. Nazwa musi być unikatowa i możliwy do utrwalenia.  
  
 `dwFlags`  
 [in] Flagi, które są skojarzone z nazwanego elementu. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Wskazuje, że nazwa elementu jest dostępne w przestrzeni nazw skryptu. Dzięki temu dostęp do zdarzeń, metod i właściwości elementu.<br /><br /> Konwencja właściwości elementu obejmują elementy podrzędne elementu. W związku z tym wszystkie właściwości obiektu podrzędnego i metody (i ich elementy podrzędne, rekursywnie) są dostępne.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Wskazuje źródło elementu zdarzeń czy skrypt może mieć skryptu procedury obsługi zdarzeń.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Wskazuje, czy element jest kolekcją globalnych właściwości i metod, które są skojarzone ze skryptem. Jej elementów członkowskich są tworzone jako zmienne globalne i metod.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Wskazuje, czy element ma zostać zapisany po zapisaniu skryptu tworzenia aparatu.|  
|SCRIPTITEM_CODEONLY|0x00000200|Wskazuje, że element nazwany reprezentuje obiekt tylko kod i nie ma członka do autora.|  
|SCRIPTITEM_NOCODE|0x00000400|Wskazuje, że nazwany element jest tylko nazwa dodawany i go nie ma nic do autora.|  
  
 `pdisp`  
 [in] `IDispatch` z `NamedItem` obiektu, który jest używany do gromadzenia metod, właściwości lub źródło zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)