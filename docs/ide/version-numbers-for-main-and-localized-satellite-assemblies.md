---
title: "Numery wersji dla głównych i zlokalizowanych zestawów satelickich | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e2f2e76d9dec25e6c5bf5d6deeab42364d28de8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Numery wersji dla głównych i zlokalizowanych zestawów satelickich
<xref:System.Resources.SatelliteContractVersionAttribute> Klasa obsługuje przechowywanie wersji zestawu głównego, który używa zlokalizowane zasoby za pomocą Menedżera zasobów. Stosowanie <xref:System.Resources.SatelliteContractVersionAttribute> do aplikacji główny zestaw pozwala zaktualizować i ponownie wdróż bez aktualizowania jego zestawy satelickie zestawu. Na przykład można użyć <xref:System.Resources.SatelliteContractVersionAttribute> klasy z dodatkiem service pack, który nie wprowadzenia nowych zasobów, bez odbudowywania ani ponownego wdrażania ponownie zestawy satelickie. Zlokalizowanych zasobów była dostępna, musi odpowiadać wersji kontraktu satelickiego zestawu głównego <xref:System.Reflection.AssemblyVersionAttribute> klasy z zestawami satelity. Należy określić numer dokładnej wersji w <xref:System.Resources.SatelliteContractVersionAttribute>; symbol wieloznaczny znaków, takich jak "*" nie są dozwolone. Aby uzyskać więcej informacji, zobacz [podczas pobierania zasobów](/dotnet/framework/resources/retrieving-resources-in-desktop-apps).  
  
## <a name="updating-assemblies"></a>Aktualizowanie zestawów  
 <xref:System.Resources.SatelliteContractVersionAttribute> Klasa umożliwia zaktualizowanie główny zestaw bez konieczności aktualizacji z zestawu satelickiego lub na odwrót. Po zaktualizowaniu główny zestaw jej numer wersji zestawu zostanie zmieniona. Jeśli chcesz nadal używać istniejących zestawów satelickich zmienić numer wersji zestawu głównego, ale numer wersji kontraktu satelity pozostaną bez zmian. Na przykład w Twojej wersji pierwszej wersji główny zestaw może być 1.0.0.0. Wersji kontraktu satelickiego i wersja zestawu z zestawu satelickiego będzie również 1.0.0.0. Jeśli musisz zaktualizować Twojego główny zestaw z dodatkiem Service Pack, można zmienić wersję zestawu na 1.0.0.1, przy jednoczesnym zachowaniu wersji kontraktu satelickiego i wersja zestawu satelity jako 1.0.0.0.  
  
 Jeśli musisz zaktualizować zestaw satelicki, ale nie zestawie głównym, należy zmienić <xref:System.Reflection.AssemblyVersionAttribute> zestawu satelity. Wraz z zestawu satelickiego należy wysłać zestaw zasad, stwierdzający, że Twoje nowe zestawu satelickiego jest zgodna z Twoje stare zestawu satelickiego. Aby uzyskać więcej informacji dotyczących zasad, zobacz [jak zestawy środowiska wykonawczego lokalizuje](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
 Poniższy kod przedstawia sposób ustawiania wersji kontraktu satelickiego. Kod można umieścić w skrypcie kompilacji lub plik AssemblyInfo.vb lub AssemblyInfo.cs.  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Jak lokalizuje zestawów przez środowisko uruchomieniowe](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)   
 [Ustawienie atrybutów zestawu](/dotnet/framework/app-domains/set-assembly-attributes)   
 [Zabezpieczenia a zlokalizowane zestawy satelickie](../ide/security-and-localized-satellite-assemblies.md)   
 [Lokalizowanie aplikacji](../ide/localizing-applications.md)   
 [Globalizacja i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md)