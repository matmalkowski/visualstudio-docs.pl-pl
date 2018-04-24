---
title: 'Porady: ignorowanie błędów w zadaniach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild - "vs-ide-sdk"
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.openlocfilehash: 348a026815d0d48390fed5741e6dba741fda9937
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-ignore-errors-in-tasks"></a>Porady: ignorowanie błędów w zadaniach
Czasami ma kompilacji jako odporna na błędy w niektórych zadań. Jeśli te zadania niekrytyczne zakończą się niepowodzeniem, które mają kompilacji, aby kontynuować, ponieważ nadal powodują wymagane dane wyjściowe. Na przykład, jeśli projekt używa `SendMail` zadanie, aby wysłać wiadomość e-mail po utworzeniu każdego składnika można rozważyć go akceptowalne dla kompilacji przejść do ukończenia, nawet w przypadku serwerów poczty są niedostępne i nie można wysyłać komunikaty o stanie. Lub, na przykład, jeśli plików pośrednich zwykle są usuwane podczas kompilacji, można rozważyć go akceptowalne dla kompilacji przejść do ukończenia, nawet wtedy, gdy nie można usunąć tych plików.  
  
## <a name="using-the-continueonerror-attribute"></a>Za pomocą atrybutu ContinueOnError  
 `ContinueOnError` Atrybutu `Task` element określa, czy kompilacja zatrzymuje się lub będzie kontynuowane po wystąpieniu błędu zadania. Ten atrybut kontroluje również, czy błędy są traktowane jako błędy lub ostrzeżenia podczas kompilacji będzie kontynuowane.  
  
 `ContinueOnError` Atrybut może zawierać jedną z następujących wartości:  
  
-   **WarnAndContinue** lub **true**. Jeśli zadanie nie powiedzie się, kolejne zadania w [docelowej](../msbuild/target-element-msbuild.md) element i kompilacji, nadal można wykonać, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.  
  
-   **ErrorAndContinue**. Jeśli zadanie nie powiedzie się, kolejne zadania w `Target` element i kompilacji, nadal można wykonać, a wszystkie błędy z zadania są traktowane jako błędy.  
  
-   **ErrorAndStop** lub **false** (ustawienie domyślne). Jeśli zadanie nie powiedzie się, kolejnych zadań na `Target` element i kompilacji nie są wykonywane i całą `Target` element i kompilacji jest traktowane jako powiodła się.  
  
 Wersje programu .NET Framework, przed 4.5 obsługiwane tylko `true` i `false` wartości.  
  
 Wartość domyślna `ContinueOnError` jest `ErrorAndStop`. Jeśli ustawiono atrybut `ErrorAndStop`, wprowadzeniu zachowanie jawne osobom czytającym pliku projektu.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Aby zignorować błąd w zadanie  
  
-   Użyj `ContinueOnError` atrybut zadania. Na przykład:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, że `Build` docelowej nadal działa i kompilacji jest uznawany za Powodzenie, nawet jeśli `Delete` zadań kończy się niepowodzeniem.  
  
```xml  
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
[MSBuild](../msbuild/msbuild.md)  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)