---
title: IDebugSourceServerModule | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5210b819d78bcec1cac5179ac679cf201279e9fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116171"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Reprezentuje informacji o serwerze źródłowym, który jest zawarty w pliku PDB.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez aparaty debugera i używane przez debuger interfejsu użytkownika.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugSourceServerModule`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Pobiera tablicę informacji o serwerze źródłowym.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll