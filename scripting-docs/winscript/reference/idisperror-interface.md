---
title: Interfejs IDispError | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f139d317db5aa00f03f8e9abd71020e5ff35b03
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idisperror-interface"></a>Interfejs IDispError
Przedstawia informacje szczegółowe informacje o błędzie kontekstowych.  
  
> [!NOTE]
>  Ten interfejs nie jest zaimplementowana.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDispError` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Pobiera informacje o błędzie określonego typu.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Pobiera następnych `IDispError` obiektu.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Pobiera kod błędu z `IDispError` obiektu.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Zwraca identyfikator programowy zależne od języka dla klasy lub aplikacji, która wywołała błędu.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Zwraca ścieżkę pliku pomocy i identyfikator kontekstu tematu, który wyjaśni ten błąd, jeśli to możliwe.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Zwraca tekstowy opis błędu.|