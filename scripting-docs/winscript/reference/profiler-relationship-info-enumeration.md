---
title: Wyliczenie PROFILER_RELATIONSHIP_INFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f01ca5e001d45907af70b46b6dc362e8ae0b2044
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796333"
---
# <a name="profilerrelationshipinfo-enumeration"></a>Wyliczenie PROFILER_RELATIONSHIP_INFO
Reprezentuje informacje o obiektach w relacji. Używane w [struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|Obiekt jest liczbą.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|Obiekt jest ciąg.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|Obiekt jest obiektem stosu.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|Obiekt zewnętrzny, oznacza to, nie jest na stercie kolekcji pamięci.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|Obiekt jest typu BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|wartość 0x06|Obiekt jest ciąg.|