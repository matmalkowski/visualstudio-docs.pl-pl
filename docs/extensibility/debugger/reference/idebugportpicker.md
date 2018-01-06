---
title: IDebugPortPicker | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61973b6b9d7c62e8276f46443d0b9520419d3934
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Reprezentuje dostosowany interfejs użytkownika wyboru portu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawców portu. Dostawca portu definiuje ich selektora portu ujawnienie go jako identyfikatora CLSID i wskazujący `metricPortPickerCLSID` metryki na CLSID uwidocznione.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugPortPicker`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Wyświetla okno dialogowe określony, który umożliwia użytkownikowi wybranie portu.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Ustawia dostawcę usługi.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll