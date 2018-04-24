---
title: 'Porady: kompilacja określonych obiektów docelowych w rozwiązaniach za pomocą MSBuild.exe | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89c14c73a4ed49f8fa78422d151d526990359a15
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Porady: kompilacja określonych obiektów docelowych w rozwiązaniach za pomocą programu MSBuild.exe
MSBuild.exe umożliwia kompilacja określonych obiektów docelowych określonych projektów w rozwiązaniu.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Aby utworzyć określony element docelowy określonego projektu w rozwiązaniu  
  
1.  W wierszu polecenia wpisz `MSBuild.exe <SolutionName>.sln`, gdzie `<SolutionName>` odpowiada nazwie pliku rozwiązania, który zawiera element docelowy, który chcesz wykonać.  
  
2. Określ cel po `/target:` przełącznika w formacie **`ProjectName`** `:` **`TargetName`**. Jeśli nazwa projektu zawiera którykolwiek ze znaków `%`, `$`, `@`, `;`, `.`, `(`, `)`, lub `'`, zastąp je za pomocą `_` w określonym Nazwa docelowego.
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje `Rebuild` docelowy `NotInSlnFolder` projektu, a następnie wykonuje `Clean` docelowy `InSolutionFolder` projektu, który znajduje się w `NewFolder` folder rozwiązania.  
  
```
msbuild SlnFolders.sln /target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean`
```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli chcesz sprawdzić dostępne opcje, służy opcja debugowania udostępniane przez MSBuild Aby to zrobić. Ustaw zmienną środowiskową `MSBUILDEMITSOLUTION=1` i Skompiluj rozwiązanie. Spowoduje to utworzenie pliku programu MSBuild o nazwie `<SolutionName>.sln.metaproj` wewnętrzny widok rozwiązania programu MSBuild w którym wyświetlana podczas kompilacji. Możesz sprawdzić ten widok, aby ustalić, jakie elementy docelowe są dostępne dla kompilacji.

Nie Konstruuj z tej zmiennej środowiskowej ustawić, chyba że potrzebne w tym widoku wewnętrznego. To ustawienie może spowodować problemy z kompilacją projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz też  
 [Informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [ MSBuild](../msbuild/msbuild.md)  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
