---
title: IDebugModuleLoadEvent2::GetModule | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dcf01689b6ab133ee52870ff65293ab31e98855e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628669"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugModuleLoadEvent2::GetModule](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmoduleloadevent2-getmodule).  
  
Pobiera moduł, który jest załadowany lub zwolnione.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pModule`  
 [out] Zwraca [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) obiekt, który reprezentuje ładowanie lub zwalnianie modułu.  
  
 `pbstrDebugMessage`  
 [out w] Zwraca wartość opcjonalną wiadomość, zawierająca opis tego zdarzenia. Jeśli ten parametr ma wartość null, jest wymagany żaden komunikat.  
  
 `pbLoad`  
 [out w] Wartość różną od zera (`TRUE`) Jeśli moduł jest ładowanie i zero (`FALSE`) Jeśli Trwa zwalnianie modułu. Jeśli ten parametr ma wartość null, wymagane jest Brak stanu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)

