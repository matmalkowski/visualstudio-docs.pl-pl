---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e2ce262b219b46d543389ac6a8ae8d71466419f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Kompiluje i uruchamia określony projekt lub rozwiązanie, a następnie zamyka zintegrowane środowisko programistyczne (IDE).

## <a name="syntax"></a>Składnia

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumenty
 `SolutionName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

 `ProjectName`

 Wymagana. Pełna ścieżka i nazwa pliku projektu.

## <a name="remarks"></a>Uwagi
 Kompiluje i uruchamia określony projekt lub rozwiązanie zgodnie z ustawieniami określonymi dla aktywnej konfiguracji rozwiązania. Ten przełącznik minimalizuje IDE podczas projekt lub rozwiązanie jest uruchamiana i zamyka IDE po projektu lub rozwiązania zakończy działanie.

-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

-   Podsumowanie informacji, w tym błędy, mogą być wyświetlane w **polecenia** okna, lub określić za pomocą pliku dziennika `/out` przełącznika.

## <a name="example"></a>Przykład
 W tym przykładzie jest uruchamiany rozwiązania `MySolution` w IDE w trybie zminimalizowanym za pomocą konfiguracji aktywnych wdrożeń, a następnie zamyka IDE.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Uruchom (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)