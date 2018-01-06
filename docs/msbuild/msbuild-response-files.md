---
title: Pliki odpowiedzi MSBuild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
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
caps.latest.revision: "3"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d2d204535d24fc1ef000c897f45bdb51710dfee9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-response-files"></a>Pliki odpowiedzi MSBuild
Pliki odpowiedzi (.rsp —) są pliki tekstowe zawierające MSBuild.exe przełączniki wiersza polecenia. Każdy przełącznik może być w oddzielnym wierszu lub wszystkich przełączników mogą być w jednym wierszu. Wiersze komentarza są poprzedzone znakiem  **#**  symbolu.  **@**  Przełącznik jest używany do przekazania do MSBuild.exe inny plik odpowiedzi.  
  
 Plik autoodpowiedzi jest specjalne .rsp — plik używający MSBuild.exe automatycznie podczas kompilowania projektu. Ten plik MSBuild.rsp, musi być w tym samym katalogu co MSBuild.exe, w przeciwnym razie go nie zostaną znalezione. Możesz edytować ten plik, aby określić domyślny przełączniki wiersza polecenia do MSBuild.exe. Na przykład, jeśli używasz tego samego rejestratora za każdym razem, gdy w przypadku kompilowania projektu, można dodać **/logger** Przełącz się do MSBuild.rsp i MSBuild.exe użyje rejestratora za każdym razem, gdy projekt jest budowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)