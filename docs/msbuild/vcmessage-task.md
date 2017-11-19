---
title: "Vcmessage — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 16ed7f4207a65915afbf18a496a0152e04e9a8d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="vcmessage-task"></a>VCMessage — Zadanie
Dzienniki ostrzeżenia i komunikaty o błędach podczas kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 To zadanie ułatwia wdrożenie programu MSBuild w języku Visual C++ i nie jest przeznaczona do wywoływania przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **vcmessage —** zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**Argumenty**|Opcjonalne **ciąg** parametru.<br /><br /> Rozdzielana średnikami lista komunikatów do wyświetlenia.|  
|**Kod**|Wymagane **ciąg** parametru.<br /><br /> Numer błędu, które kwalifikują się komunikatu.|  
|**Typ**|Opcjonalne **ciąg** parametru.<br /><br /> Określa typ wiadomości emisji. Określ `"Warning"` można wyemitować komunikat ostrzegawczy lub `"Error"` można wyemitować komunikat o błędzie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)