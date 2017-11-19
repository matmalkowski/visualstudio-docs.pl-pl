---
title: Interfejs IScriptNode | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-interface"></a>Interfejs IScriptNode
Obiekt, który implementuje `IScriptNode` interfejsu reprezentuje strony sieci Web.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IScriptNode` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Wskazuje, czy obiekt jest nadal aktywne.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Dodaje wystąpienie podrzędne `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Dodaje skryptlet jako wystąpienie podrzędne `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Usuwa drzewa obiektów.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Zwraca podrzędny, który znajduje się pod określonym indeksem w węźle.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Zwraca wartość zdefiniowanym przez aplikację, używanego do kojarzenia skryptlet z obiektu hosta.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Zwraca indeks obiektu w lista elementów podrzędnych elementu nadrzędnego.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Zwraca język skryptów, który jest używany przez bieżący węzeł skryptu.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Zwraca liczbę węzłów podrzędnych `IScriptNode` obiektu.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Zwraca `IScriptNode` obiekt, który jest elementem nadrzędnym obiektu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)