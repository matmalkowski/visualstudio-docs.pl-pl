---
title: Vcmessage — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8ef67a4fa19bd715e73e50fcc268aee7a4df5d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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