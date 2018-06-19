---
title: Pliki odpowiedzi MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f685364bbcf69b8d4b91635cb42079f3f06e5311
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31571009"
---
# <a name="msbuild-response-files"></a>Pliki odpowiedzi MSBuild
Pliki odpowiedzi (.rsp —) są pliki tekstowe zawierające MSBuild.exe przełączniki wiersza polecenia. Każdy przełącznik może być w oddzielnym wierszu lub wszystkich przełączników mogą być w jednym wierszu. Wiersze komentarza są poprzedzone znakiem **#** symbolu. **@** Przełącznik jest używany do przekazania do MSBuild.exe inny plik odpowiedzi.  
  
## <a name="msbuildrsp"></a>MSBuild.rsp
Plik autoodpowiedzi jest specjalne .rsp — plik używający MSBuild.exe automatycznie podczas kompilowania projektu. Ten plik MSBuild.rsp, musi być w tym samym katalogu co MSBuild.exe, w przeciwnym razie go nie zostaną znalezione. Możesz edytować ten plik, aby określić domyślny przełączniki wiersza polecenia do MSBuild.exe. Na przykład, jeśli używasz tego samego rejestratora za każdym razem, gdy w przypadku kompilowania projektu, można dodać **/logger** Przełącz się do MSBuild.rsp i MSBuild.exe użyje rejestratora za każdym razem, gdy projekt jest budowany.  

## <a name="directorybuildrsp"></a>Directory.Build.rsp
W wersji 15,6 i powyżej MSBuild przeszuka katalogi nadrzędne projektu dla pliku o nazwie `Directory.Build.rsp`.  Może to być przydatne w repozytorium kodu źródłowego musi podać argumenty domyślne podczas kompilacji z wiersza polecenia.  Można go również służyć do określ argumenty wiersza polecenia hostowanej kompilacji.

## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)