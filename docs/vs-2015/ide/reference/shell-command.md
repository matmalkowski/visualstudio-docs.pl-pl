---
title: Polecenia powłoki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a7b3b8d5e2e86dd613d16c1bcec8d6819765eeb8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676582"
---
# <a name="shell-command"></a>Shell — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [polecenia powłoki](https://docs.microsoft.com/visualstudio/ide/reference/shell-command).  
  
  
Uruchamia programy wykonywalne z poziomu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## <a name="arguments"></a>Argumenty  
 `path`  
 Wymagane. Ścieżka i nazwa pliku do wykonania lub dokument, aby otworzyć. Pełna ścieżka jest wymagana, jeśli określony plik nie znajduje się w jednym z katalogów w zmiennej środowiskowej PATH.  
  
 `args`  
 Opcjonalna. Argumenty do przekazania do wywoływanej program.  
  
## <a name="switches"></a>Przełączniki  
 /commandwindow [i] / Command [i] /c [i] / cmd  
 Opcjonalna. Określa, czy dane wyjściowe dla pliku wykonywalnego, który jest wyświetlany w **polecenia** okna.  
  
 dir:`folder` [i] / d: `folder`  
 Opcjonalna. Określa katalog roboczy, aby ustawić, gdy program jest uruchamiany.  
  
 / outputwindow [i] / Output [i] out [i] /o  
 Opcjonalna. Określa, czy dane wyjściowe dla pliku wykonywalnego, który jest wyświetlany w **dane wyjściowe** okna.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić przełączników /c dir /o natychmiast po `Tools.Shell`. Cokolwiek określona po nazwę pliku wykonywalnego, który jest przekazywany do niego jako argumenty wiersza polecenia.  
  
 Wstępnie zdefiniowane alias `Shell` mogą być używane zamiast `Tools.Shell`.  
  
> [!CAUTION]
>  Jeśli `path` argument dostarcza ścieżkę katalogu, a także nazwę pliku, całą nazwę ścieżki należy ująć w cudzysłów literału ("" "), jak w następujących czynności:  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 Każdy zestaw trzech podwójnego cudzysłowu ("" ") jest interpretowany przez `Shell` procesora jako znak, pojedynczy cudzysłów. W związku z tym, w poprzednim przykładzie przekazuje faktycznie poniższy ciąg ścieżki, aby `Shell` polecenia:  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  Jeśli użytkownik nie należy umieszczać ciąg ścieżki w cudzysłowie literału ("" "), pierwszą przestrzeń Windows będzie można użyć tylko część ciągu. Na przykład jeśli ciąg ścieżki powyżej nie zostały podane prawidłowo, Windows będzie szukać pliku o nazwie "Program" znajdujący się w katalogu głównym C:\. Plik wykonywalny C:\Program.exe była rzeczywiście dostępne, nawet jeśli jest on instalowane przez nielegalnego naruszeniem Windows podejmował próbę wykonania tego programu, zamiast programu żądaną "c:\Program Files\SomeFile.exe".  
  
## <a name="example"></a>Przykład  
 Następujące polecenie używa xcopy.exe można skopiować pliku `MyText.txt` do `Text` folderu. Dane wyjściowe z xcopy.exe jest wyświetlany w obu **okna polecenia** i **dane wyjściowe** okna.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Okno danych wyjściowych](../../ide/reference/output-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



