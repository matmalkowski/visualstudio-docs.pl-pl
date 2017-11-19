---
title: "SETENV — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 0223d57cf4c16166149b1fc9e8903f563b724d20
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="setenv-task"></a>SetEnv — Zadanie
Ustawia lub usuwa wartość zmiennej określonego środowiska.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **SetEnv** zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**Nazwa**|Wymagane **ciąg** parametru.<br /><br /> Nazwa zmiennej środowiskowej.|  
|**OutputEnvironmentVariable**|Opcjonalne **ciąg** parametru wyjściowego.<br /><br /> Zawiera wartość, która jest przypisana do zmiennej środowiskowej, która jest określona przez **nazwa** parametru.|  
|**Prefiks**|Obowiązkowe `Boolean` parametru.<br /><br /> Jeśli `true`, łączy wartość **wartość** parametru przed wartością zmiennej środowiskowej, która jest określona przez **nazwa** parametr, a następnie przypisuje wynik do środowiska Zmienna. Jeśli `false`, przypisuje tylko wartość **wartość** parametr do zmiennej środowiskowej.|  
|**Docelowy**|Opcjonalne **ciąg** parametru.<br /><br /> Określa lokalizację, w której jest przechowywana wartość zmiennej środowiskowej. Określ "`User`"lub"`Machine`".<br /><br /> Aby uzyskać więcej informacji, zobacz "EnvironmentVariableTarget wyliczenie" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**Wartość**|Opcjonalne **ciąg** parametru.<br /><br /> Wartość przypisana do zmiennej środowiskowej, która jest określona przez **nazwa** parametru. Jeśli **wartość** jest pusty i istnieje zmienna, usunąć zmiennej. Jeśli zmienna nie istnieje, nie występuje błąd, nawet jeśli nie można wykonać operacji.<br /><br /> Aby uzyskać więcej informacji, zobacz "Metoda Environment::SetEnvironmentVariable" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)