---
title: "Porady: kompilacja określonych obiektów docelowych w rozwiązaniach za pomocą MSBuild.exe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: "10"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 58033b13f7201039dbfdc5e45d912a509da818d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Porady: kompilacja określonych obiektów docelowych w rozwiązaniach za pomocą programu MSBuild.exe
MSBuild.exe umożliwia kompilacja określonych obiektów docelowych określonych projektów w rozwiązaniu.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Aby utworzyć określony element docelowy określonego projektu w rozwiązaniu  
  
1.  W wierszu polecenia wpisz `MSBuild.exe <SolutionName>.sln`, gdzie `<SolutionName>` odpowiada nazwie pliku rozwiązania, który zawiera element docelowy, który chcesz wykonać.  
  
2.  Określ cel po **/t** przełącznika w formacie *ProjectName*:*TargetName*.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje `Rebuild` docelowy `NotInSlnFolder` projektu, a następnie wykonuje `Clean` docelowy `InSolutionFolder` projektu, który znajduje się w `NewFolder` folder rozwiązania.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)