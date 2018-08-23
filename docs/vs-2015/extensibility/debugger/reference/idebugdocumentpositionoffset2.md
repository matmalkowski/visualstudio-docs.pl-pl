---
title: IDebugDocumentPositionOffset2 | Dokumentacja firmy Microsoft
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
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d10c71340b6ad6c7e76753b40c3bef55d8e7e606
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683864"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugDocumentPositionOffset2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentpositionoffset2).  
  
Reprezentuje pozycji w pliku źródłowym jako przesunięcie znaku.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Implementowany przez środowisko IDE, są używane przez aparaty debugowania.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugDocumentPositionOffset2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Getrange —](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Pobiera zakres dla bieżącej pozycji dokumentu.|  
  
## <a name="remarks"></a>Uwagi  
 Spowoduje to zwrócenie te same informacje co [getrange —](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ale w `char` powoduje przesunięcie od początku dokumentu. Przedstawia dokumentu, takie jak jego istniałby na dysku, oznacza to Jednowymiarowa tablica znaków, a nie informacji wierszy i kolumn, który zazwyczaj jest zwracany.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

