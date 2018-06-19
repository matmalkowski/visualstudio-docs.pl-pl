---
title: Shell — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04ec2719b57f387633a7244d7089be963d3ba87c
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704106"
---
# <a name="shell-command"></a>Shell — Polecenie
Uruchamia programy wykonywalne z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Składnia

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Argumenty
 `path`

 Wymagana. Nazwa i ścieżka pliku pliku do wykonania lub dokument, aby otworzyć. Pełna ścieżka jest wymagany, jeśli określony plik nie jest w jednym z katalogów w zmiennej środowiskowej PATH.

 `args`

 Opcjonalna. Argumenty do przekazania do wywoływanej program.

## <a name="switches"></a>Przełączniki
 /commandwindow [i] / Command [i] /c [i] / cmd

 Opcjonalna. Określa, czy dane wyjściowe dla pliku wykonywalnego, który jest wyświetlany w **polecenia** okna.

 dir:`folder` [i] / d: `folder`

 Opcjonalna. Określa katalog roboczy, aby ustawić, gdy program jest uruchamiany.

 /outputwindow [i] / Output [i] / out [i] /o

 Opcjonalna. Określa, czy dane wyjściowe dla pliku wykonywalnego, który jest wyświetlany w **dane wyjściowe** okna.

## <a name="remarks"></a>Uwagi
 Należy określić przełączników /c /o dir natychmiast po `Tools.Shell`. Cokolwiek określona po nazwie pliku wykonywalnego jest przekazywany do niego jako argumenty wiersza polecenia.

 Wstępnie zdefiniowane alias `Shell` można użyć zamiast `Tools.Shell`.

> [!CAUTION]
> Jeśli `path` argument dostarcza ścieżki katalogu, a także nazwę pliku, całą nazwę ścieżki należy ująć w cudzysłowy literału ("" ") w następujących czynności:


```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

 Każdy zestaw trzy znaki cudzysłowu ("" ") jest interpretowany przez `Shell` procesora jako znak pojedynczego cudzysłowu. W związku z tym w poprzednim przykładzie przekazuje faktycznie następujący ciąg ścieżki `Shell` polecenia:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Jeśli ciąg ścieżki nie ująć w cudzysłowy literału ("" "), systemu Windows można będzie użyć tylko część ciągu pierwszego obszaru. Na przykład jeśli ciąg ścieżki powyżej nie zostały podane prawidłowo, system Windows będzie szukać plik o nazwie "Program" znajduje się w katalogu głównym C:\. Jeśli plik wykonywalny C:\Program.exe zostały faktycznie dostępne, nawet co zainstalowany przez nielegalnemu naruszeniu systemu Windows będzie próba wykonania tego programu, zamiast żądanego "c:\Program Files\SomeFile.exe" program.


## <a name="example"></a>Przykład
 Polecenie używa xcopy.exe można skopiować pliku `MyText.txt` do `Text` folderu. Dane wyjściowe z xcopy.exe jest wyświetlany zarówno **okno polecenia** i **dane wyjściowe** okna.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Okno Dane wyjściowe](../../ide/reference/output-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)