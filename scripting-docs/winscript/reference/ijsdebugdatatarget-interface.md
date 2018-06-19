---
title: Ijsdebugdatatarget — interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94e158ced0da6d59bfcadeb87bf206c94a6099ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794938"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget — Interfejs
Implementowana przez debuger umożliwiają korzystanie z funkcji dostępu i zmiany stanu procesu docelowego debugera.  
  
## <a name="syntax"></a>Składnia  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory — metoda](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Rezerwuje i/lub zatwierdza obszaru pamięci w wirtualnej przestrzeni adresowej procesu docelowego.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator — metoda](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Tworzy moduł wyliczający dla ramki stosu.|  
|[IJsDebugDataTarget::FreeVirtualMemory — metoda](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Zwalnia i/lub decommits obszaru pamięci w wirtualnej przestrzeni adresowej procesu docelowego.|  
|[IJsDebugDataTarget::GetThreadContext — metoda](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Pobiera kontekst dla danego wątku.|  
|[IJsDebugDataTarget::GetTlsValue — metoda](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Pobiera wartość w miejscu magazynu lokalnego (TLS) wątku dla określonego indeksu TLS debugowany wątek.|  
|[IJsDebugDataTarget::ReadBSTR — metoda](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Odczytuje BSTR z docelowego debugowania.|  
|[IJsDebugDataTarget::ReadMemory — metoda](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Odczytuje pamięci procesu docelowego.|  
|[IJsDebugDataTarget::ReadNullTerminatedString — metoda](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Odczytuje określoną liczbę znaków z elementem docelowym.|  
|[IJsDebugDataTarget::WriteMemory — metoda](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Odczytuje pamięci procesu docelowego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)