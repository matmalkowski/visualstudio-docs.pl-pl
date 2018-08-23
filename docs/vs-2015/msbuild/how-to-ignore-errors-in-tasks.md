---
title: 'Porady: ignorowanie błędów w zadaniach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 186662f9c9bca72ca7ee840d1f2efc6437a7ccc4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676745"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Porady: ignorowanie błędów w zadaniach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: ignorowanie błędów w zadaniach](https://docs.microsoft.com/visualstudio/msbuild/how-to-ignore-errors-in-tasks).  
  
  
Czasami chcesz być odporne na błędy w wykonywaniu pewnych zadań kompilacji. Jeśli te krytyczne zadania nie powiedzie się, które mają kompilacji, aby kontynuować, ponieważ nadal może utworzyć wymagane dane wyjściowe. Na przykład, jeśli projekt używa `SendMail` zadanie, aby wysłać wiadomość e-mail po utworzeniu każdego składnika, warto rozważyć je dopuszczalny dla kompilacji przejść do ukończenia, nawet wtedy, gdy serwery poczty są niedostępne i nie można wysłać komunikaty o stanie. Lub, na przykład, jeśli pliki pośrednie zwykle są usuwane podczas kompilacji, można rozważyć jej dopuszczalny dla kompilacji przejść do ukończenia, nawet wtedy, gdy nie można usunąć tych plików.  
  
## <a name="using-the-continueonerror-attribute"></a>Za pomocą ContinueOnError — atrybut  
 `ContinueOnError` Atrybutu `Task` element kontroluje, czy kompilacja zatrzymuje się lub być kontynuowana po wystąpieniu awarii zadań. Ten atrybut określa również, czy błędy są traktowane jako błędy lub ostrzeżenia, gdy kontynuuje kompilację.  
  
 `ContinueOnError` Atrybut może zawierać jedną z następujących wartości:  
  
-   **WarnAndContinue** lub **true**. Jeśli zadanie nie powiedzie się, kolejne zadania w [docelowej](../msbuild/target-element-msbuild.md) elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.  
  
-   **ErrorAndContinue**. Jeśli zadanie nie powiedzie się, kolejne zadania w `Target` elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.  
  
-   **ErrorAndStop** lub **false** (ustawienie domyślne). Jeśli zadanie nie powiedzie się, kolejnych zadań na `Target` elementu i kompilacja nie są wykonywane i całą `Target` elementu i kompilacja jest uważany za nie powiodło się.  
  
 Wersje programu .NET Framework przed 4.5 obsługiwane tylko `true` i `false` wartości.  
  
 Wartość domyślna `ContinueOnError` jest `ErrorAndStop`. Jeśli ten atrybut zostanie ustawiony `ErrorAndStop`, wprowadzeniu zachowanie jawne dla każdego, kto czyta pliku projektu.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Ignorowanie błędu w zadaniu  
  
-   Użyj `ContinueOnError` atrybut zadania. Na przykład:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, że `Build` docelowej nadal działa i kompilacja, jest uznawany za sukces, nawet jeśli `Delete` zadań kończy się niepowodzeniem.  
  
```  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też
[MSBuild](msbuild.md)  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)


