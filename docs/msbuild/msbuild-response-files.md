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
ms.openlocfilehash: 83f8e5ad4522a47eaea978b14678fe134b4faa8e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081595"
---
# <a name="msbuild-response-files"></a>Pliki odpowiedzi MSBuild
Odpowiedź (*rsp*) pliki to pliki tekstowe, które zawierają *MSBuild.exe* przełączniki wiersza polecenia. Każdy przełącznik może być w oddzielnym wierszu lub wszystkich przełączników mogą znajdować się na jeden wiersz. Komentarz wiersze są poprzedzone znakiem **#** symboli. **@** Przekazać inny plik odpowiedzi, który jest używany przełącznik *MSBuild.exe*.  
  
## <a name="msbuildrsp"></a>MSBuild.rsp
Plik odpowiedzi automatyczne jest specjalny *rsp* pliku, który *MSBuild.exe* automatycznie używa podczas kompilowania projektu. Ten plik *MSBuild.rsp*, musi znajdować się w tym samym katalogu co *MSBuild.exe*, w przeciwnym razie go nie zostanie znaleziony. Możesz edytować ten plik, aby określić domyślny wiersz polecenia zmienia się na *MSBuild.exe*. Na przykład, jeśli używasz tego samego rejestrowania za każdym razem, gdy tworzysz projekt, można dodać **/logger** przełączyć się do *MSBuild.rsp*, i *MSBuild.exe* użyje rejestratora każdym Projekt został skompilowany.  

## <a name="directorybuildrsp"></a>Directory.Build.rsp
W wersji 15.6 i nowszym MSBuild wyszuka katalogi nadrzędne projektu dla pliku o nazwie *Directory.Build.rsp*.  Może to być przydatne w repozytorium kodu źródłowego w celu zapewnienia domyślnych argumentów podczas kompilacji z wiersza polecenia.  Może również służyć do określić argumenty wiersza polecenia hostowanych kompilacji.

## <a name="see-also"></a>Zobacz także  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md)