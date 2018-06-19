---
title: IApplicationDebugger::CreateInstanceAtDebugger | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6495c2d8782d1128700bdfb6d4081b80ffae878
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793885"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Umożliwia tworzenie obiektów w procesie debuger przez kod będący poza procesem do debugera.  
  
> [!IMPORTANT]
>  Tej metody nie powinny być implementowane, ponieważ pozwala niezaufanym kod w celu utworzenia dowolnego obiektów w wątku zaufanych debugera.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 [in] Identyfikator (CLSID) można utworzyć obiektu klasy.  
  
 `pUnkOuter`  
 [in] Jeśli `NULL`, obiekt nie jest tworzony jako część agregacji. W przeciwnym razie `pUnkOuter` jest wskaźnik do obiektu agregacji `IUnknown` interfejsu (kontrolowanie `IUnknown`).  
  
 `dwClsContext`  
 [in] Kontekst do uruchomienia kodu wykonywalnego. Wartości te są pobierane z wyliczenia `CLSCTX`.  
  
 `riid`  
 [in] Identyfikator interfejsu używany do komunikacji z obiektem.  
  
 `ppvObject`  
 [out] Adres wskaźnika zmienna, która odbiera wskaźnika interfejsu w `riid`. Po pomyślnym powrocie *`ppvObject` znajduje się wskaźnik żądanego interfejsu. W przypadku awarii \* `ppvObject` zawiera `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda deleguje do `CoCreateInstance`.  
  
 Metoda nie jest obecnie zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)