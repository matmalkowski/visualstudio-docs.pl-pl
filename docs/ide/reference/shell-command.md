---
title: Polecenia powłoki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: 0c44f6c784b33a927741a09c3dffc9b13017488e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="shell-command"></a>Shell — Polecenie
Uruchamia programy wykonywalne z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## <a name="arguments"></a>Argumenty  
 `path`  
 Wymagany. Nazwa i ścieżka pliku pliku do wykonania lub dokument, aby otworzyć. Pełna ścieżka jest wymagany, jeśli określony plik nie jest w jednym z katalogów w zmiennej środowiskowej PATH.  
  
 `args`  
 Opcjonalny. Argumenty do przekazania do wywoływanej program.  
  
## <a name="switches"></a>Przełączniki  
 /commandwindow [i] / Command [i] /c [i] / cmd  
 Opcjonalny. Określa, czy dane wyjściowe dla pliku wykonywalnego, który jest wyświetlany w **polecenia** okna.  
  
 dir:`folder` [i] / d: `folder`  
 Opcjonalny. Określa katalog roboczy, aby ustawić, gdy program jest uruchamiany.  
  
 /outputwindow [i] / Output [i] / out [i] /o  
 Opcjonalny. Określa, czy dane wyjściowe dla pliku wykonywalnego, który jest wyświetlany w **dane wyjściowe** okna.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić przełączników /c /o dir natychmiast po `Tools.Shell`. Cokolwiek określona po nazwie pliku wykonywalnego jest przekazywany do niego jako argumenty wiersza polecenia.  
  
 Wstępnie zdefiniowane alias `Shell` można użyć zamiast `Tools.Shell`.  
  
> [!CAUTION]
>  Jeśli `path` argument dostarcza ścieżki katalogu, a także nazwę pliku, całą nazwę ścieżki należy ująć w cudzysłowy literału ("" ") w następujących czynności:  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 Każdy zestaw trzy znaki cudzysłowu ("" ") jest interpretowany przez `Shell` procesora jako znak pojedynczego cudzysłowu. W związku z tym w poprzednim przykładzie przekazuje faktycznie następujący ciąg ścieżki `Shell` polecenia:  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  Jeśli ciąg ścieżki nie ująć w cudzysłowy literału ("" "), systemu Windows można będzie użyć tylko część ciągu pierwszego obszaru. Na przykład jeśli ciąg ścieżki powyżej nie zostały podane prawidłowo, system Windows będzie szukać plik o nazwie "Program" znajduje się w katalogu głównym C:\. Jeśli plik wykonywalny C:\Program.exe zostały faktycznie dostępne, nawet co zainstalowany przez nielegalnemu naruszeniu systemu Windows będzie próba wykonania tego programu, zamiast żądanego "c:\Program Files\SomeFile.exe" program.  
  
## <a name="example"></a>Przykład  
 Polecenie używa xcopy.exe można skopiować pliku `MyText.txt` do `Text` folderu. Dane wyjściowe z xcopy.exe jest wyświetlany zarówno **okno polecenia** i **dane wyjściowe** okna.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Okno danych wyjściowych](../../ide/reference/output-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)