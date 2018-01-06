---
title: IDebugProcessSecurity | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7acdb0f16182ebca904229d7620b80f5ec81d1de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity`jest implementowana przez dostawcę portu z ostrzeżeniem, że dołączanie do procesu jest niebezpieczne.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugProcessSecurity`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Pobiera nazwę użytkownika od dostawcy portu.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Ostrzega użytkownika, że dołączanie do procesu debugowania jest niebezpieczne.|  
  
## <a name="remarks"></a>Uwagi  
 Implementuje ten interfejs, aby wyświetlić ostrzeżenie i Zezwalaj użytkownikowi na Anuluj, jeśli proces, do którego jest podłączany mogą być uważane za niebezpieczne.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Porty](../../../extensibility/debugger/ports.md)   
 [Port dostawcy](../../../extensibility/debugger/port-suppliers.md)   
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)