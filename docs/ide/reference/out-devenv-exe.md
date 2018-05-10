---
title: -Out (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 623f4e8a8a2f6e275c42507aa3839106f3a1dd2f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Określa plik do przechowywania i wyświetlania błędów podczas uruchamiania, utworzyć, odbudować lub wdrożyć rozwiązanie.

## <a name="syntax"></a>Składnia

```cmd
devenv /out FileName
```

## <a name="arguments"></a>Argumenty
 `FileName`

 Wymagana. Ścieżka i nazwa pliku do odbierania błędy podczas kompilowania pliku wykonywalnego.

## <a name="remarks"></a>Uwagi
 Jeśli określono nazwę pliku, który nie istnieje, plik jest tworzony automatycznie. Jeśli plik już istnieje, wyniki są dołączane do istniejącej zawartości pliku.

 Błędy kompilacji wiersza polecenia są wyświetlane w **polecenia** okno i konstruktora rozwiązania widok **dane wyjściowe** okna. Ta opcja jest przydatna, jeśli są uruchomione nienadzorowanej kompilacji i powinny być wyświetlane wyniki.

## <a name="example"></a>Przykład
 W tym przykładzie jest uruchamiany `MySolution` i zapisuje błędy do pliku `MyErrorLog.txt`.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Uruchom (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Wdróż (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)