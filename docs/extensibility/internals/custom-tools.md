---
title: Niestandardowe narzędzia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f215cfbd5113377e7a98439976a7f44215eee02
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128887"
---
# <a name="custom-tools"></a>Narzędzia niestandardowe
*Narzędzia niestandardowe* można skojarzyć narzędzie z elementu w projekcie i uruchamiania tego narzędzia, zawsze, gdy plik jest zapisywany. Niektóre narzędzia niestandardowe czasami określane jako *generatory pojedynczego pliku*, są często używane do implementowania tłumaczy, które generują kod z danych i na odwrót. Na przykład utworzyć generatory pojedynczego pliku [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] kod pliki .settings i .resx poza źródłowy. Kod źródłowy wygenerowanego zapewnia wymagająca dostępu do danych w pliku .settings i resx. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typy projektu obswługują narzędzi niestandardowych; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] typów projektów nie. Swój własny typ projektu może również obsługiwać narzędzi niestandardowych.  
  
 Narzędzia niestandardowe są zarejestrowanych składników, które implementują `IVsSingleFileGenerator` interfejsu.  
  
 Narzędzia niestandardowe są skojarzone z `ProjectItem` interfejsu obiektu i przypominają projektantów i edytory. Niestandardowe narzędzie przyjmuje pliku reprezentowany przez `ProjectItem` jako argument wejściowy i zapisuje nowy plik, którego nazwa pliku jest obsługiwane przez `DefaultExtension` metody.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie generatorów jednoplikowych](../../extensibility/internals/implementing-single-file-generators.md)  
 Informacje dotyczące używania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejs do implementacji narzędzia niestandardowego.  
  
 [Rejestrowanie generatorów jednoplikowych](../../extensibility/internals/registering-single-file-generators.md)  
 Zawiera opisy wszystkie wpisy rejestru dla narzędzia niestandardowego.  
  
 [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 W tym artykule wyjaśniono, jak systemów projektów zapewniają obsługę wizualnych projektantów do dostępu do wygenerowanych klas i typów za pomocą plików tymczasowych przenośny plik wykonywalny (PE).  
  
 [Utrwalanie właściwości elementu projektu](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Pokazuje, jak można utrwalić właściwości elementu projektu, takie jak autor pliku źródłowego, w pliku projektu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Zawiera szczegółowe informacje na temat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, który przekształca pojedynczego pliku wejściowego w pojedynczym wyjściowym pliku kompilacji lub dodane do projektu.  
  
 <xref:EnvDTE.ProjectItem>  
 Wyjaśniono `ProjectItem` interfejs, który reprezentuje element w projekcie.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Zawiera szczegółowe informacje na temat `DefaultExtension` metodę, która pobiera rozszerzenie nazwy pliku, który znajduje się na nazwę pliku wyjściowego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie projektów](../../extensibility/extending-projects.md)  
 Informacje dotyczące używania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty i rozwiązania można organizować pliki kodu i plików zasobów i implementowania kontroli źródła.