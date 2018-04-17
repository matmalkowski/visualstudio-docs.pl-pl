---
title: Zarządzanie właściwościami projektów i rozwiązań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a68cc558a52f7c8d66f76600cd68309ad67769c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="managing-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań

Projekty mają właściwości, które będą zarządzały sposobem wiele aspektów kompilacji, debugowanie, testowania i wdrażania. Niektóre właściwości są wspólne dla wszystkich typów projektów, a niektóre są unikatowe dla określonego języka lub platformy. Dostęp do właściwości projektu prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierając pozycję **właściwości**, lub wpisując "właściwości" w **Szybkie uruchamianie** pole wyszukiwania na pasku menu.

![Menu kontekstowe projektu](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")

Projekty .NET mogą także mieć węzeł właściwości w drzewo projektu.

![Właściwości węzła drzewa Eksploratora rozwiązań](../ide/media/vs2015_props_se.png "VS2015_Props_SE")

## <a name="project-properties"></a>Właściwości projektu

Właściwości projektu są zorganizowane w grupy, a każda grupa ma swoją własną stronę właściwości. Strony może być różna dla różnych języków i typów projektów.

### <a name="c-visual-basic-and-f-projects"></a>Projektów C#, VB i F #

W projektach C#, VB i F #, właściwości są widoczne w **projektanta projektu**. Na poniższej ilustracji przedstawiono stronę właściwości kompilacji w projekcie WPF w języku C#:

![Projektant projektu programu Visual Studio](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")

Aby uzyskać informacje o poszczególnych stron właściwości w Projektancie projektu, zobacz [odwołanie do właściwości projektu](../ide/reference/project-properties-reference.md).

> [!TIP]
> Rozwiązania ma kilka właściwości i dlatego projektu elementów; te właściwości są dostępne w [okna właściwości](../ide/reference/properties-window.md), a nie **projektanta projektu**.

### <a name="c-and-javascript-projects"></a>Projekty C++ i JavaScript

Projekty C++ i JavaScript ma inny użytkownik interfejsu do zarządzania właściwości projektu. Na ilustracji przedstawiono strony właściwości projektu C++ (stron JavaScript są podobne):

![Visual C&#43; &#43; właściwości projektu](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")

Informacji o właściwościach projektu C++, zobacz [Praca z właściwości projektu (C++)](/cpp/ide/working-with-project-properties). Aby uzyskać więcej informacji o właściwościach JavaScript, zobacz [strony właściwości, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Właściwości rozwiązania

Aby uzyskać dostęp do właściwości w ramach rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**. W oknie dialogowym można ustawić konfiguracje projektu do debugowania lub Wersja kompilacji, wybierz projekty, do których powinny być projekt startowy po naciśnięciu klawisza F5 i ustaw opcje analizy kodu.

## <a name="see-also"></a>Zobacz także

[Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
