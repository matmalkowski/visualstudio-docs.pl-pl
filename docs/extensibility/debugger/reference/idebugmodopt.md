---
title: IDebugModOpt | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 77b542731f247c9f092ad9ee79f41da3ef0df373
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodopt"></a>IDebugModOpt
Reprezentuje modyfikujący opcjonalne debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskane z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt, który reprezentuje klasy lub metody.  
  
## <a name="methods"></a>Metody  
 Ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Pobiera listę modyfikatorów opcjonalne.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll