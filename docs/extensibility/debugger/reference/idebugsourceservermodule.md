---
title: IDebugSourceServerModule | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: caf51056af3172e5dd13c551bf61d9780e407b1e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll