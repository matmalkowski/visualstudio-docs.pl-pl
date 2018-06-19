---
title: IDebugDocumentTextEvents::onUpdateTextAttributes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateTextAttributes
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ea7caa1c1632e1a85e12010ec39593b8e0a6d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794359"
---
# <a name="idebugdocumenttexteventsonupdatetextattributes"></a>IDebugDocumentTextEvents::onUpdateTextAttributes
Wskazuje, czy zmieniono atrybuty tekstu skojarzone z podstawowym zakres pozycji znaku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 [in] Pozycja znaku pierwszego znaku, który zmieniono atrybuty.  
  
 `cNumToUpdate`  
 [in] Liczba znaków w zakresie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Tej metody oznacza, że tekst atrybuty skojarzone z podstawowym zakresu znaków w pozycji ma zmieniony.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)