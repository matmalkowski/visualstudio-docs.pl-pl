---
title: Pliki odpowiedzi MSBuild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7520a9f51f0d9420039728a75e84d4ed16583738
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-response-files"></a>Pliki odpowiedzi MSBuild
Pliki odpowiedzi (.rsp —) są pliki tekstowe zawierające MSBuild.exe przełączniki wiersza polecenia. Każdy przełącznik może być w oddzielnym wierszu lub wszystkich przełączników mogą być w jednym wierszu. Wiersze komentarza są poprzedzone znakiem  **#**  symbolu. **@**  Przełącznik jest używany do przekazania do MSBuild.exe inny plik odpowiedzi.  
  
 Plik autoodpowiedzi jest specjalne .rsp — plik używający MSBuild.exe automatycznie podczas kompilowania projektu. Ten plik MSBuild.rsp, musi być w tym samym katalogu co MSBuild.exe, w przeciwnym razie go nie zostaną znalezione. Możesz edytować ten plik, aby określić domyślny przełączniki wiersza polecenia do MSBuild.exe. Na przykład, jeśli używasz tego samego rejestratora za każdym razem, gdy w przypadku kompilowania projektu, można dodać **/logger** Przełącz się do MSBuild.rsp i MSBuild.exe użyje rejestratora za każdym razem, gdy projekt jest budowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)