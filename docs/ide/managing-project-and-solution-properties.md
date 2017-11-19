---
title: "Zarządzanie właściwościami projektów i rozwiązań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d1f725429e1b63be097a4563ab9e26d1f374cc61
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań
Projekty mają właściwości, które będą zarządzały sposobem wiele aspektów kompilacji, debugowanie, testowania i wdrażania. Niektóre właściwości są wspólne dla wszystkich typów projektów, a niektóre są unikatowe dla określonego języka lub platformy. Dostęp właściwości projektu prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierając pozycję właściwości lub wpisując właściwości do **szybkiego uruchamiania** pole wyszukiwania na pasku menu.  
  
 ![Menu kontekstowe projektu](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")  
  
 Projekty .NET mogą także mieć węzeł właściwości w drzewo projektu.  
  
 ![Właściwości węzła drzewa Eksploratora rozwiązań](../ide/media/vs2015_props_se.png "VS2015_Props_SE")  
  
> [!TIP]
>  Rozwiązania ma kilka właściwości i dlatego projektu elementów; te właściwości są dostępne w [okna właściwości](../ide/reference/properties-window.md), a nie **projektanta projektu**.  
  
## <a name="project-properties"></a>Właściwości projektu  
 Właściwości projektu są zorganizowane w grupy i każda grupa ma swoją własną stronę właściwości i strony może być różna dla różnych języków i typów projektów.  
  
### <a name="c-visual-basic-and-f-projects"></a>Projektów C#, VB i F #  
 W projektach C#, VB i F #, właściwości są widoczne w **projektanta projektu**. Na poniższej ilustracji przedstawiono stronę właściwości kompilacji w projekcie WPF w języku C#:  
  
 ![Projektant projektu programu Visual Studio](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")  
  
 Aby uzyskać informacje o poszczególnych stron właściwości w Projektancie projektu, zobacz [odwołanie do właściwości projektu](../ide/reference/project-properties-reference.md).  
  
### <a name="c-and-javascript-projects"></a>Projekty C++ i JavaScript  
 Projekty C++ i JavaScript ma inny użytkownik interfejsu do zarządzania właściwości projektu. Na ilustracji przedstawiono strony właściwości projektu C++ (stron JavaScript są podobne):  
  
 ![Visual C &43; &#43; Właściwości projektu](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")  
  
 Informacji o właściwościach projektu C++, zobacz [Praca z właściwościami projektu](/cpp/ide/working-with-project-properties). Aby uzyskać więcej informacji o właściwościach JavaScript, zobacz [strony właściwości, JavaScript](../ide/reference/property-pages-javascript.md).  
  
## <a name="solution-properties"></a>Właściwości rozwiązania  
 Aby uzyskać dostęp do właściwości w ramach rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**. W oknie dialogowym można ustawić konfiguracje projektu do debugowania lub Wersja kompilacji, wybierz projekty, do których powinny być projekt startowy po naciśnięciu klawisza F5 i ustaw opcje analizy kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
