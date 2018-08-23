---
title: IDebugPortPicker | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b92f188dd2bed678e4117adde7c61d8844e8360
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677268"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugPortPicker](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportpicker).  
  
Reprezentuje dostosowanego interfejsu użytkownika dotyczące wybierania portu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawców portu. Dostawcy portu definiuje ich selektora portu przez uwidaczniania go jako identyfikatora CLSID i wskazanie `metricPortPickerCLSID` metryki na narażonych CLSID.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugPortPicker`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Zostanie wyświetlone okno dialogowe określonego, który umożliwia użytkownikowi wybranie portu.|  
|[Setsite —](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Ustawia dostawcę usług.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

