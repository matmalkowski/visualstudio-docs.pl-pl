---
title: "Stackframetypeenum — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4dcb46fc2fb3936e0cee91426b4787945bd14f59
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Określa typ ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Elementy  
 `FrameTypeFPO`  
 Wskaźnik ramki pominięta; FPO informacji.  
  
 `FrameTypeTrap`  
 Ramka pułapki jądra.  
  
 `FrameTypeTSS`  
 Ramka pułapki jądra.  
  
 `FrameTypeStandard`  
 Standardowe EBP ramki stosu.  
  
 `FrameTypeFrameData`  
 Wskaźnik ramki pominięta; Ramki danych informacji.  
  
 `FrameTypeUnknown`  
 Ramki, który nie ma żadnych informacji debugowania.  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie wartości są zwracane przez wywołanie do [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)