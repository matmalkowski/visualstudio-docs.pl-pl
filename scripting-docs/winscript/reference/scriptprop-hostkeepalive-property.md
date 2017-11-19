---
title: "Właściwość SCRIPTPROP_HOSTKEEPALIVE | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="scriptprophostkeepalive-property"></a>Właściwość SCRIPTPROP_HOSTKEEPALIVE
Służy do określenia, czy aparat skryptów powinny być przechowywane funkcjonalnej, jeśli istnieją oczekujące odwołania.  
  
 Użyj [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) Aby ustawić tę właściwość `true`. Jeśli ta właściwość jest ustawiona na `true`, aparat skryptów są przechowywane w pełni funkcjonalny, tak długo, jak istnieje co najmniej jedno oczekujące odwołanie do samego aparatu skryptów lub `IDispatch` wskaźnika do obiektu JavaScript utworzone za pomocą skryptów aparat. Jeśli ta właściwość jest skonfigurowana `true`, należy nie jawnie zamknąć lub zresetuj aparat skryptu za pomocą [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) lub [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) metody. Wersja ostatnie odwołanie do obiektu skryptu zamyka aparat skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Wymagania  
 Ta właściwość jest wyświetlana tylko w wersji activscp.idl, który jest instalowany z [!INCLUDE[win8](../../javascript/includes/win8-md.md)], z 2707082 KB programu Internet Explorer 8 na [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], lub za pomocą 2722913 KB dla programu Internet Explorer 9 na [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] lub [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].