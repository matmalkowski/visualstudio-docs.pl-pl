---
title: Vcmessage — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/27/2018
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
ms.openlocfilehash: 66c245f78c27521e9db53327f8dfdc567ed0e995
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154142"
---
# <a name="vcmessage-task"></a>VCMessage — Zadanie
Dzienniki, ostrzeżenia i komunikaty o błędach podczas kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 To zadanie ułatwia Implementowanie MSBuild dla języka Visual C++ i nie jest przeznaczona do wywoływania przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **vcmessage —** zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**Argumenty**|Opcjonalnie **ciąg** parametru.<br /><br /> Rozdzielana średnikami lista wiadomości do wyświetlenia.|  
|**Kod**|Wymagane **ciąg** parametru.<br /><br /> Numer błędu, który kwalifikuje wiadomości.|  
|**Typ**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa rodzaj komunikatów do emitowania. Określ "Ostrzeżenie", aby emitować komunikat ostrzegawczy lub "Error", aby emitować komunikat o błędzie.|  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)