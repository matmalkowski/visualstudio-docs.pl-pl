---
title: Interfejs IScriptEntry | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a785be8777cf3400f7723c24f1022bad6e22e330
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795097"
---
# <a name="iscriptentry-interface"></a>Interfejs IScriptEntry
Obiekt, który implementuje `IScriptEntry` interfejsu reprezentuje blok skryptu albo obiektem funkcji.  
  
 Oprócz dziedziczone z metody `IScriptNode`, `IScriptEntry` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Zwraca tekst, który odpowiada do treści `IScriptEntry` blok skryptu, bloku funkcji lub skryptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Zwraca nazwę elementu, który identyfikuje `IScriptEntry` obiektu.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|W przypadku wpisów, które reprezentują pojedynczego obiektu (na przykład funkcja) zwraca nazwę obiektu.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Zwraca długość hasła i pozycji początkowej.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Zwraca typ informacji o `IScriptEntry` obiekt funkcji.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Zwraca tekst, który odpowiada `IScriptEntry` bloku skryptu lub kodu źródłowego, który jest zawarty w `IScriptScriptlet` obsługi zdarzeń.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Ustawia tekst, który znajduje się w treści `IScriptEntry` bloku skryptu lub `IScriptScriptlet` skryptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Ustawia nazwę elementu, który identyfikuje `IScriptEntry` obiektu.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Wpisów, które reprezentują pojedynczego obiektu (na przykład funkcja) Określa nazwę obiektu.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Ustawia typ informacji o `IScriptEntry` obiekt funkcji.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Ustawia tekst, który odpowiada `IScriptEntry` bloku skryptu lub kodu źródłowego, który jest zawarty w `IScriptScriptlet` obsługi zdarzeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)