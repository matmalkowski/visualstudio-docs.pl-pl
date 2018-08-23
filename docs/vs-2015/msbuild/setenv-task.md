---
title: SETENV — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccd67a4bf70e05f0661277db05430615afbcfdad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681046"
---
# <a name="setenv-task"></a>SetEnv — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [SETENV — zadanie](https://docs.microsoft.com/visualstudio/msbuild/setenv-task).  
  
  
Ustawia lub usuwa wartość określonej zmiennej środowiskowej.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **SetEnv** zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**Nazwa**|Wymagane **ciąg** parametru.<br /><br /> Nazwa zmiennej środowiskowej.|  
|**OutputEnvironmentVariable**|Opcjonalnie **ciąg** parametr wyjściowy.<br /><br /> Zawiera wartość, która jest przypisana do zmiennej środowiskowej, który jest określony przez **nazwa** parametru.|  
|**Prefiks**|Obowiązkowe `Boolean` parametru.<br /><br /> Jeśli `true`, łączy wartości **wartość** parametru przed wartością zmiennej środowiskowej, który jest określony przez **nazwa** parametru, a następnie przypisuje wynik do środowiska Zmienna. Jeśli `false`, przypisuje wartość elementu **wartość** parametr do zmiennej środowiskowej.|  
|**Docelowy**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa lokalizację przechowywania dla zmiennej środowiskowej. Określ "`User`"or"`Machine`".<br /><br /> Aby uzyskać więcej informacji, zobacz "EnvironmentVariableTarget Enumeration" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**Wartość**|Opcjonalnie **ciąg** parametru.<br /><br /> Wartość przypisana do zmiennej środowiskowej, który jest określony przez **nazwa** parametru. Jeśli **wartość** jest pusta i zmienna istnieje, zmienna zostanie usunięty. Jeśli zmienna nie istnieje, nie występuje błąd, mimo że nie można wykonać operacji.<br /><br /> Aby uzyskać więcej informacji, zobacz opis "Environment::SetEnvironmentVariable metody" [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)



