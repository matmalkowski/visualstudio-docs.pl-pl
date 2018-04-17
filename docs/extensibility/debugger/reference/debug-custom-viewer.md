---
title: DEBUG_CUSTOM_VIEWER | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84d8bdc7a4ea9ac59ee0956226618402b397844b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Struktura, która identyfikuje podglądu niestandardowego lub wpisz wizualizatora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwID  
 Identyfikator możesz rozróżnić wiele przeglądarek lub wizualizatorów zaimplementowana przez jedną `GUID`.  
  
 bstrMenuName  
 Tekst, który będzie wyświetlany w menu rozwijanym.  
  
 bstrDescription  
 Opis podglądu niestandardowego lub typ wizualizatora (musi być wartością null, jeśli nie jest używany).  
  
 guidLang  
 Język udostępnienie ewaluatora wyrażenia.  
  
 guidVendor  
 Dostawca udostępnienie ewaluatora wyrażenia.  
  
 bstrMetric  
 Metryki, pod którym podglądu niestandardowego lub typ wizualizatora `CLSID` jest przechowywany.  
  
## <a name="remarks"></a>Uwagi  
 Lista ta struktura jest zwracany przez wywołanie do [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) — metoda (i przez rozszerzenie, [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metody).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)