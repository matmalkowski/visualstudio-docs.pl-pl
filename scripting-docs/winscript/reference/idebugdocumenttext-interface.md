---
title: Interfejs IDebugDocumentText | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9522d1075cd796fb69f6abbc42adc2706a817fed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794539"
---
# <a name="idebugdocumenttext-interface"></a>Interfejs IDebugDocumentText
Zapewnia dostęp do wersji tylko tekst dokumentu debugowania. Ten interfejs obowiązują następujące zasady:  
  
-   Zarówno pozycji znaku i numery wierszy są wartości początkowej zero.  
  
-   Położenie znaku reprezentują przesunięcia znaku; nie reprezentują bajtów lub word przesunięcia. W przypadku systemu Win32 pozycji znaku jest przesunięcie Unicode.  
  
 Oprócz dziedziczone z metody `IDebugDocument`, `IDebugDocumentText` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Zwraca atrybuty dokumentu.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Zwraca liczbę wierszy i liczbę znaków w dokumencie.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Zwraca pozycji znaku odpowiadający znakowi pierwszego wiersza.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Zwraca numer wiersza i, opcjonalnie, Przesunięcie znaku w wierszu, który odpowiada danej pozycji znaku.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Pobiera znaki i/lub znak atrybuty skojarzone z pozycji znaku zakresu.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Zwraca zakres pozycji znaku odpowiadający kontekstu dokumentu.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Tworzy obiekt kontekstu dokumentu odpowiadającego zakresowi pozycji podany znak.|