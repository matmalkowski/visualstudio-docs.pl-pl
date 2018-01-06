---
title: "Użycie wielu procesorów w projektach kompilacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c2879b753ecdf06779403b01bbeb0681448759fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-multiple-processors-to-build-projects"></a>Używanie wielu procesorów w projektach kompilacji
Program MSBuild potrafi optymalnie wykorzystywać komputery z wieloma procesorami lub procesorami wielordzeniowymi. Dla każdego dostępnego procesora jest tworzony oddzielny proces kompilacji. Jeśli na przykład system ma cztery procesory, powstają cztery procesy kompilacji. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]może jednocześnie przetwarzać tych kompilacji, a w związku z tym całkowity czas kompilacji zostanie zmniejszona. Jednak kompilowanie równoległe wprowadza pewne zmiany w przebiegu procesów kompilacji. Omówiono je w tym temacie.  
  
## <a name="project-to-project-references"></a>Projekt do odwołania się do projektu  
 Gdy [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] napotka odwołanie projektu do projektu (P2P), podczas gdy używa równoległe kompilacje do tworzenia projektu, zbudował odwołanie tylko jeden raz. Jeśli dwa projekty mają to samo odwołanie P2P, nie będzie ono kompilowane osobno dla każdego projektu. Zamiast tego aparat kompilacji zwraca to samo odwołanie P2P do obu projektów, które go używają. Na przyszłe żądania o ten sam element docelowy w trakcie jednej sesji jest podawane to samo odwołanie P2P.  
  
## <a name="cycle-detection"></a>Wykrywanie cyklu  
 Wykrywanie cyklu działa tak samo jak w programie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, z wyjątkiem który teraz [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może raportować wykrywanie cyklu w innym czasie lub w kompilacji.  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>Błędy i wyjątki podczas kompilacji równoległych  
 W kompilacjach równoległych błędy i wyjątki mogą się wydarzyć o innym czasie niż podczas kompilacji nierównoległej i gdy jeden projekt nie jest kompilowany, druga kompilacja trwa dalej. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]nie spowoduje zatrzymania kompilacji dowolnego projektu, która tworzy równolegle z jedną, która nie powiodła się. Nadal innych projektów do kompilacji, dopóki nie powiedzie się lub nie. Jednak jeśli włączono opcję <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, kompilacje nie będą zatrzymywane nawet mimo wystąpienia błędów.  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Projektu programu Visual C++ (.vcproj) i pliki rozwiązania (.sln)  
 Zarówno [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów (VCPROJ) i pliki rozwiązania (sln) mogą zostać przekazane do [zadanie programu MSBuild](../msbuild/msbuild-task.md). Dla [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów, VCWrapperProject jest wywoływana, a następnie wewnętrzną [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt zostanie utworzony. Dla [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] rozwiązań SolutionWrapperProject jest tworzony i następnie wewnętrznej [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt zostanie utworzony. W obu przypadkach powstały projekt jest traktowany tak samo jak każdy inny projekt programu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## <a name="multi-process-execution"></a>Wykonanie etapu wieloprocesowego  
 Prawie wszystkie czynności dotyczące kompilacji wymagają, aby bieżący katalog pozostał bez zmian przez cały proces kompilacji, ponieważ zapobiega to błędom związanym ze ścieżką. W związku z tym projektów nie można uruchamiać w różnych wątkach programu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], ponieważ spowodowałoby to utworzenie wielu katalogów.  
  
 Aby zabiec temu problemowi, ale nadal umożliwiać kompilowanie na wielu procesorach, program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stosuje „izolację procesów”. Za pomocą tego mechanizmu program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może utworzyć maksymalnie `n` procesów, gdzie `n` odpowiada liczbie procesorów dostępnych w komputerze. Jeśli na przykład program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kompiluje rozwiązanie na komputerze, który ma dwa procesory, zostaną utworzone tylko dwa procesy kompilacji. Procesy te są wykonywane wielokrotnie w celu skompilowania wszystkich projektów w rozwiązaniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [Zadania](../msbuild/msbuild-tasks.md)