---
title: SETENV — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.setenv
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec47adec3a9c979a21a543f2c073c440384b26d1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31572182"
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
|**docelowy**|Opcjonalne **ciąg** parametru.<br /><br /> Określa lokalizację, w której jest przechowywana wartość zmiennej środowiskowej. Określ "`User`"lub"`Machine`".<br /><br /> Aby uzyskać więcej informacji, zobacz "EnvironmentVariableTarget wyliczenie" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**Wartość**|Opcjonalne **ciąg** parametru.<br /><br /> Wartość przypisana do zmiennej środowiskowej, która jest określona przez **nazwa** parametru. Jeśli **wartość** jest pusty i istnieje zmienna, usunąć zmiennej. Jeśli zmienna nie istnieje, nie występuje błąd, nawet jeśli nie można wykonać operacji.<br /><br /> Aby uzyskać więcej informacji, zobacz "Metoda Environment::SetEnvironmentVariable" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)