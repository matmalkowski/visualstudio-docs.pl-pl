---
title: span::span — Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afd383dfd03a1e4e0a2ca9c377ce372d1586c738
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="spanspan-constructor"></a>span::span — Konstruktor
Inicjuje nowe wystąpienie klasy `span` klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
span(  
   const marker_series& _Series,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Series`  
 Kontekst serii prawidłowy znacznik.  
  
 `_Format`  
 Ciąg formatu złożony, który zawiera tekst zmieszać zero lub więcej elementów formatu, które odnoszą się do obiektów na liście argumentów.  
  
 `_Importance`  
 Poziom ważności.  
  
 `_Category`  
 Kategoria.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkersobj.h  
  
 **Namespace:** CONCURRENCY::Diagnostic —
 
 ## <a name="see-also"></a>Zobacz też
 [span, klasa](../profiling/span-class.md)