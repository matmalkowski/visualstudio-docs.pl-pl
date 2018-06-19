---
title: 'Porady: Konfigurowanie obiektów docelowych i zadań | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a09f2ec1af511cb789f2101e2df0a675dd065e8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31578416"
---
# <a name="how-to-configure-targets-and-tasks"></a>Porady: konfigurowanie obiektów docelowych i zadań
Do uruchomienia w środowisku, które ich elementami docelowymi, niezależnie od środowiska na komputerze deweloperskim można ustawić wybranego zadania programu MSBuild. Na przykład gdy używasz 64-bitowym komputerze do tworzenia aplikacji danej architektury 32-bitowych obiektów docelowych wybranych zadań są uruchamiane w procesie 32-bitowych.  
  
> [!NOTE]
>  Jeśli zadania kompilacji jest napisany w języku .NET, takie jak Visual C# lub Visual Basic i nie używa natywne zasoby lub narzędzi, a następnie zostanie uruchomiony w dowolnym kontekście docelowego bez dostosowania.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>Atrybuty UsingTask i parametry zadania  
 Następujące `UsingTask` atrybuty wpływają na wszystkie operacje w procesie kompilacji określonego zadania:  
  
-   `Runtime` Atrybut, jeśli jest obecny, ustawia wspólnej wersję języka wspólnego (CLR) i możliwe jest któregokolwiek z następujących wartości: `CLR2`, `CLR4`, `CurrentRuntime`, lub `*` (wszystkie środowiska uruchomieniowego).  
  
-   `Architecture` Atrybut, jeśli jest obecny, ustawia platformy i liczba bitów i można wykonać jedną z następujących wartości: `x86`, `x64`, `CurrentArchitecture`, lub `*` (dowolnej architekturze).  
  
-   `TaskFactory` Atrybut, jeśli jest obecny, ustawia fabryki zadań, które tworzy i uruchamia wystąpienie zadania i przyjmuje tylko wartość `TaskHostFactory`. Aby uzyskać więcej informacji zobacz sekcję fabryki zadań w dalszej części tego dokumentu.  
  
```xml  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Można również użyć `MSBuildRuntime` i `MSBuildArchitecture` parametrów, aby ustawić kontekst docelowy pojedynczego zadania.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Przed MSBuild uruchamia zadanie, wygląda pasujący `UsingTask` z tym samym kontekście docelowej.  Parametry, które są określone w `UsingTask` , ale nie znajduje się w odpowiednich zadań są traktowane jako do dopasowania.  Parametry, które określone zadania, ale nie w odpowiedniej `UsingTask` są także traktowane jako do dopasowania. Jeśli nie określono wartości parametru albo `UsingTask` lub zadań, wartości domyślnych do `*` (żadnych parametrów).  
  
> [!WARNING]
>  Jeśli istnieje więcej niż jedna `UsingTask` istnieje i mieć pasujące `TaskName`, `Runtime`, i `Architecture` atrybuty, ostatnią ma zostać obliczone zastępuje inne.  
  
 Jeśli ustawiono parametrów w zadaniu, próbuje odnaleźć MSBuild `UsingTask` odpowiada tych parametrów albo, co najmniej nie jest w konflikcie z nich.  Więcej niż jeden `UsingTask` można określić kontekst docelowy tego samego zadania.  Na przykład zadanie, które ma różne pliki wykonywalne dla środowisk inny element docelowy może wyglądać tego:  
  
```xml  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## <a name="task-factories"></a>Fabryki zadań  
 Przed uruchomieniem zadania, MSBuild sprawdza, czy jest on wybrany do obsługiwania w bieżącym kontekście oprogramowania.  Jeśli wyznaczona zadanie programu MSBuild przekazuje ją do AssemblyTaskFactory, który uruchamia go w bieżącym procesie; w przeciwnym razie program MSBuild przekazuje zadanie TaskHostFactory, na którym uruchamiane jest zadanie w ramach procesu odpowiadającego kontekst docelowy. Nawet wtedy, gdy bieżący kontekst i kontekst docelowy są zgodne, można wymusić uruchomienie zadania out-of-process (w przypadku izolacji, zabezpieczeń lub z innych powodów) przez ustawienie `TaskFactory` do `TaskHostFactory`.  
  
```xml  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>Parametry zadania fantomu  
 Wszelkie inne parametry zadań, takich jak `MSBuildRuntime` i `MSBuildArchitecture` można ustawić właściwości kompilacji.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 W przeciwieństwie do innych parametrów zadania `MSBuildRuntime` i `MSBuildArchitecture` nie są widoczne dla samo zadanie.  Można zapisać zadania, które jest świadome kontekst, w której jest uruchamiane, musisz przetestować kontekście wywoływania programu .NET Framework lub właściwości kompilacji służy do przekazywania informacji kontekstu za pomocą innych parametrów zadania.  
  
> [!NOTE]
>  `UsingTask` atrybuty można skonfigurować przy użyciu właściwości zestaw narzędzi i środowiska.  
  
 `MSBuildRuntime` i `MSBuildArchitecture` parametry zapewniają najbardziej elastyczny sposób, aby ustawić kontekst docelowy, ale także najbardziej ograniczonym w zakresie.  Z jednej strony ponieważ są ustawione na wystąpienie zadania, sama i nie są oceniane, aż zadanie zostanie uruchomiony, mogą dziedziczyć wartości z pełnego zakresu właściwości dostępne pod adresem zarówno w czasie oceny, jak i w czasie kompilacji.  Z drugiej strony parametry te dotyczą tylko konkretne wystąpienie zadań w określonej lokalizacji docelowej.  
  
> [!NOTE]
>  Parametry zadania są obliczane w kontekście węzła nadrzędnego, a nie w kontekście hosta zadań. Zmienne środowiskowe, które są zależne środowiska uruchomieniowego lub architektura, które (takie jak lokalizacja plików programu) będzie obliczać wartość odpowiadającą węzła nadrzędnego.  Jednak jeśli bezpośrednio przez zadanie jest do odczytu tej zmiennej środowiskowej, ona poprawnie ocenia się w kontekście hosta zadań.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie obiektów docelowych i zadań](../msbuild/configuring-targets-and-tasks.md)
