---
title: IDebugCustomViewer::DisplayValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 74990eac497b8ed239894121eb954cd8eeca55e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Ta metoda jest wywoływana do wyświetlenia określonej wartości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hwnd`  
 [in] Okno nadrzędne  
  
 `dwID`  
 [in] Identyfikator dla niestandardowych przeglądarek, które obsługują więcej niż jednego typu.  
  
 `pHostServices`  
 [in] Zastrzeżone. Zawsze ustawiony na wartość null.  
  
 `pDebugProperty`  
 [in] Interfejs, który może służyć do pobierania wartości do wyświetlenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wyświetlanie ma "modalnego" Ta metoda będzie utworzyć niezbędne okna, Wyświetl wartość czeka na wprowadzenie danych i zamknij okno, wszystkie przed zwróceniem do obiektu wywołującego. Oznacza to, że metoda musi obsługiwać wszystkich aspektów wyświetlanie wartość właściwości z tworzenia okna danych wyjściowych Trwa oczekiwanie na dane wejściowe użytkownika, aby niszczenie okna.  
  
 Umożliwia zmianę wartości w danej [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) obiektu, można użyć [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) — metoda — Jeśli wartość może zostać wyrażona jako ciąg. W przeciwnym razie konieczne jest utworzenie niestandardowego interfejsu — wyłącznie dla ewaluatora wyrażeń, to implementacja `DisplayValue` metoda — na tym samym obiekcie, który implementuje `IDebugProperty3` interfejsu. Ten niestandardowy interfejs musi dostarczać zmieniające danych dowolnego rozmiar lub złożoność.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)