---
title: Wyliczenie SCRIPTLANGUAGEVERSION | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="scriptlanguageversion-enumeration"></a>Wyliczenie SCRIPTLANGUAGEVERSION
Określa możliwości skryptów wersji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Wersja domyślna. Wartość całkowita jest 0.|  
|SCRIPTLANGUAGEVERSION_5_7|W wersji 5.7 skryptów systemu Windows. Wartość całkowita jest 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Wersja 5.8 skryptów systemu Windows. Wartość całkowita jest 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Maksymalna wersja. Wartość całkowita wynosi 255.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kody błędów, wyliczenia i stałe aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)