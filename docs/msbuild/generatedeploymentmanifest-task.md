---
title: Generatedeploymentmanifest — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1eb989972f8cfd2e44516b798c25e5f579e5f66
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31571480"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest — Zadanie

Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania opisano wdrożenie aplikacji, definiując unikatową tożsamość wdrożenia, identyfikujące cech wdrożenia, takich jak instalacji lub w trybie online, określając aplikacji zaktualizuj ustawienia i lokalizacje, aktualizacji i wskazujący odpowiadającego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `GenerateDeploymentManifest` zadań.

|Parametr|Opis|
|---------------|-----------------|
|`AssemblyName`|Opcjonalne `String` parametru.<br /><br /> Określa `Name` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowany na podstawie `EntryPoint` lub `InputManifest` parametrów. Jeśli nie można wywnioskować nazwy, zadanie zgłasza błąd.|
|`AssemblyVersion`|Opcjonalne `String` parametru.<br /><br /> Określa `Version` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zadanie używa wartości "1.0.0.0".|
|`CreateDesktopShortcut`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli PRAWDA, ikona jest tworzony na pulpicie podczas instalacji aplikacji ClickOnce.|
|`DeploymentUrl`|Opcjonalne `String` parametru.<br /><br /> Określa lokalizację aktualizacji dla aplikacji. Jeśli ten parametr nie jest określony, lokalizacja aktualizacji nie jest zdefiniowany dla aplikacji. Jednak jeśli `UpdateEnabled` parametr jest `true`, musi być określona lokalizacja aktualizacji. Podana wartość powinna być w pełni kwalifikowaną ścieżkę adresu URL lub ścieżką UNC.|
|`Description`|Opcjonalne `String` parametru.<br /><br /> Określa opcjonalny opis dla aplikacji.|
|`DisallowUrlActivation`|Opcjonalne `Boolean` parametru.<br /><br /> Określa, czy aplikacja mają być uruchamiane automatycznie po otwarciu przy użyciu adresu URL. Jeśli ten parametr ma `true`, aplikację można uruchomić tylko z Start menu. Wartością domyślną tego parametru jest `false`. Tych danych wejściowych ma zastosowanie tylko wtedy, gdy `Install` jest wartość parametru `true`.|
|`EntryPoint`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Wskazuje punkt wejścia dla zestawu wygenerowanego manifestu. Aby uzyskać [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania, określa tych danych wejściowych [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji.<br /><br />Jeśli `EntryPoint` parametr zadania nie jest określony, `<customHostSpecified>` znacznik jest wstawiany jako element podrzędny `<entryPoint>` tagu, na przykład:<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Można dodać zależności biblioteki DLL do manifestu aplikacji przy użyciu następujących kroków:<br /><br /> 1.  Rozpoznaj odwołania do zestawu z wywołaniem do <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2.  Przekazać dane wyjściowe poprzedniego zadania i zestawu do <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3.  Przekaż zależności za pomocą `Dependencies` parametr <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>.|
|`ErrorReportUrl`|Opcjonalne <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Określa adres URL strony sieci Web, która jest wyświetlana w oknach dialogowych podczas instalacji ClickOnce.|
|`InputManifest`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Wskazuje wejściowy dokument XML służyć jako podstawa dla generatora manifestu. Dzięki temu danych strukturalnych, takich jak niestandardowe definicje manifestu, zostaną odzwierciedlone w manifeście danych wyjściowych. Element główny dokumentu XML musi być węzłem zestawu w przestrzeni nazw asmv1.|
|`Install`|Opcjonalne `Boolean` parametru.<br /><br /> Określa, czy aplikacja zostanie zainstalowana aplikacja lub aplikacji tylko w trybie online. Jeśli ten parametr ma `true`, aplikacja zostanie zainstalowana w menu Start użytkownika i mogą zostać usunięte przy użyciu okno dialogowe Dodaj lub usuń programy. Jeśli ten parametr ma `false`, aplikacja jest przeznaczona do używania online ze strony sieci Web. Wartością domyślną tego parametru jest `true`.|
|`MapFileExtensions`|Opcjonalne `Boolean` parametru.<br /><br /> Określa, czy mapowanie rozszerzenia nazwy pliku .deploy jest używana. Jeśli ten parametr ma `true`, co plik programu jest publikowany z rozszerzeniem nazwy pliku .deploy. Ta opcja jest przydatna dla zabezpieczeń serwera sieci Web ograniczyć liczbę rozszerzeń nazw plików, które musi być odblokowany, aby włączyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji. Wartością domyślną tego parametru jest `false`.|
|`MaxTargetPath`|Opcjonalne `String` parametru.<br /><br /> Określa maksymalną dozwoloną długość ścieżki do pliku w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji. Jeśli ten parametr jest określony, ten limit jest porównywany długość ścieżki każdego pliku w aplikacji. Wszystkie elementy, które przekraczają limit spowoduje, że ostrzeżenie kompilacji. Jeśli tych danych wejściowych nie została określona lub jest równa zero, nie jest przeprowadzane żadne sprawdzanie.|
|`MinimumRequiredVersion`|Opcjonalne `String` parametru.<br /><br /> Określa, czy użytkownik może Pomiń aktualizację. Jeśli użytkownik ma wersję, która jest mniejsza niż minimalna wymagana, nie ma on opcję Pomiń aktualizację. Kiedy dotyczy tylko tych danych wejściowych wartość `Install` parametr jest `true`.|
|`OutputManifest`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa nazwę pliku manifestu wygenerowanych danych wyjściowych. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego jest wywnioskowany na podstawie tożsamości wygenerowanego manifestu.|
|`Platform`|Opcjonalne `String` parametru.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Wartość domyślna to `AnyCPU`.|
|`Product`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowany na podstawie tożsamości wygenerowanego manifestu. Ta nazwa jest używana dla nazwy skrótu w Start menu i jest częścią nazwy, która jest wyświetlana w oknie dialogowym Dodaj lub usuń programy.|
|`Publisher`|Opcjonalne `String` parametru.<br /><br /> Określa wydawcy aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowany na podstawie zarejestrowanego użytkownika lub tożsamość wygenerowanego manifestu. Ta nazwa jest używana nazwa folderu, w Start menu i jest częścią nazwy, która jest wyświetlana w oknie dialogowym Dodaj lub usuń programy.|
|`SuiteNamel`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę folderu, w menu Start, w którym znajduje się aplikacja po wdrażania ClickOnce.|
|`SupportUrl`|Opcjonalne `String` parametru.<br /><br /> Określa łącze wyświetlane w oknie dialogowym Dodaj lub usuń programy w aplikacji. Podana wartość powinna być w pełni kwalifikowaną ścieżkę adresu URL lub ścieżką UNC.|
|`TargetCulture`|Opcjonalne `String` parametru.<br /><br /> Identyfikuje kultury aplikacji i określa `Language` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja jest niezmienna kultura.|
|`TrustUrlParameters`|Opcjonalne `Boolean` parametru.<br /><br /> Określa, czy parametry ciągu zapytania URL powinna zostać udostępniona w aplikacji. Wartością domyślną tego parametru jest `false`, co oznacza, że parametry nie będzie dostępne dla aplikacji.|
|`UpdateEnabled`|Opcjonalne `Boolean` parametru.<br /><br /> Wskazuje, czy aplikacja jest włączony dla aktualizacji. Wartością domyślną tego parametru jest `false`. Ten parametr ma zastosowanie tylko w przypadku wartości `Install` parametr jest `true`.|
|`UpdateInterval`|Opcjonalne `Int32` parametru.<br /><br /> Określa interwał aktualizacji dla aplikacji. Wartością domyślną tego parametru wynosi zero. Ten parametr ma zastosowanie tylko w przypadku wartości `Install` i `UpdateEnabled` są oba parametry `true`.|
|`UpdateMode`|Opcjonalne `String` parametru.<br /><br /> Określa, czy aktualizacje powinna być sprawdzana na pierwszym planie, zanim aplikacja jest uruchomiona lub jest uruchomiona w tle co aplikacja. Ten parametr może mieć następujące wartości:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Wartością domyślną tego parametru jest `Background`. Ten parametr ma zastosowanie tylko w przypadku wartości `Install` i `UpdateEnabled` są oba parametry `true`.|
|`UpdateUnit`|Opcjonalne `String` parametru.<br /><br /> Określa jednostki `UpdateInterval` parametru. Ten parametr może mieć następujące wartości:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Ten parametr ma zastosowanie tylko w przypadku wartości `Install` i `UpdateEnabled` są oba parametry `true`.|

## <a name="remarks"></a>Uwagi

Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.GenerateManifestBase> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę parametrów klasy zadania, zobacz [klasa podstawowa zadania](../msbuild/task-base-class.md).

## <a name="see-also"></a>Zobacz też

[Zadania](../msbuild/msbuild-tasks.md)  
[GenerateApplicationManifest, zadanie](../msbuild/generateapplicationmanifest-task.md)  
[SignFile, zadanie](../msbuild/signfile-task.md)  
[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)