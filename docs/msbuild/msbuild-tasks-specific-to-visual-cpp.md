---
title: MSBuild zadania właściwe dla Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 446326fb8219183774d3f90d70a0263e0fc057e0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Zadania narzędzia MSBuild właściwe dla Visual C++
Zadania Podaj kod uruchamiany podczas procesu kompilacji. Po zainstalowaniu programu Visual C++, następujące zadania są dostępne, oprócz tych, które są instalowane z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Aby uzyskać więcej informacji, zobacz [Przegląd MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview).  
  
 Oprócz parametrów dla każdego zadania każde zadanie ma następujące parametry.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Condition`|Opcjonalne `String` parametru.<br /><br /> A `Boolean` wyrażenie który [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aparat używa w celu określenia, czy będzie można wykonać tego zadania. Aby uzyskać informacje o warunkach, które są obsługiwane przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Jeśli zadanie nie powiedzie się, kolejne zadania w [docelowej](../msbuild/target-element-msbuild.md) element i kompilacji, nadal można wykonać, a wszystkie błędy z zadania są traktowane jako ostrzeżenia<br />-   **ErrorAndContinue**. Jeśli zadanie nie powiedzie się, kolejne zadania w `Target` element i kompilacji, nadal można wykonać, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (ustawienie domyślne). Jeśli zadanie nie powiedzie się, kolejnych zadań na`Target` element i kompilacji nie są wykonywane i całą `Target` element i kompilacji są traktowane jako powiodła się.<br /><br /> Wersje programu .NET Framework, przed 4.5 obsługiwane tylko `true` i `false` wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[BscMake, zadanie](../msbuild/bscmake-task.md)|Zawijania narzędzie przeglądać informacje o konserwacji narzędzie Microsoft (bscmake.exe).|  
|[CL, zadanie](../msbuild/cl-task.md)|Opakowuje narzędzia kompilatora Visual C++ (cl.exe).|  
|[CPPClean, zadanie](../msbuild/cppclean-task.md)|Usuwa pliki tymczasowe, które MSBuild tworzy podczas tworzenia projektu Visual C++.|  
|[LIB, zadanie](../msbuild/lib-task.md)|Zawijania narzędzie Microsoft 32-bitowy Library Manager (lib.exe).|  
|[Link, zadanie](../msbuild/link-task.md)|Opakowuje narzędzia konsolidatora Visual C++ (link.exe).|  
|[MIDL, zadanie](../msbuild/midl-task.md)|Opakowuje narzędzia kompilatora Microsoft interfejsu Definition Language (MIDL) (midl.exe).|  
|[MT, zadanie](../msbuild/mt-task.md)|Zawijania narzędzie Microsoft manifestu (mt.exe).|  
|[RC, zadanie](../msbuild/rc-task.md)|Opakowuje narzędzia kompilatora zasobów systemu Windows firmy Microsoft (rc.exe).|  
|[SetEnv, zadanie](../msbuild/setenv-task.md)|Ustawia lub usuwa wartość zmiennej określonego środowiska.|  
|[VCMessage, zadanie](../msbuild/vcmessage-task.md)|Dzienniki ostrzeżenie wiadomości i komunikaty o błędach podczas kompilacji.|  
|[XDCMake, zadanie](../msbuild/xdcmake-task.md)|Zawijania narzędzie dokumentacji XML (xdcmake.exe), które scala pliki dokumentacji XML (.xdc) w pliku XML.|  
|[XSD, zadanie](../msbuild/xsd-task.md)|Zawijania narzędzie definicji schematu XML (xsd.exe), które generuje pliki schematu lub klasy ze źródła.|  
|[Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)|Zawiera opis elementów MSBuild systemu.|  
|[Zadania](../msbuild/msbuild-tasks.md)|W tym artykule opisano zadania, które są jednostkami kodu, który można łączyć, aby wygenerować kompilacji.|  
|[Wpisywanie zadania](../msbuild/task-writing.md)|Opisuje sposób tworzenia zadania.|