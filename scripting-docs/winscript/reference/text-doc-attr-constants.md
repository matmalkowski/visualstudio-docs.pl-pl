---
title: Stałe TEXT_DOC_ATTR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130895e0e70b1044fab5d5ab406f940b036c37f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796432"
---
# <a name="textdocattr-constants"></a>Stała TEXT_DOC_ATTR
Opisuje atrybuty dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Stałe  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Dokument jest przeznaczony tylko do odczytu.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Dokument jest plikiem podstawowym tego drzewa dokumentu.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Dokument jest pracownika.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Dokument jest plik skryptu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)