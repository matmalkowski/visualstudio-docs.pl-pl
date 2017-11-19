---
title: "Rozwiązywanie zestawów w czasie projektowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 7ce11fb27959f5d468e08f6967b53ac079a2a28e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="resolving-assemblies-at-design-time"></a>Rozwiązywanie zestawów w czasie projektowania
Po dodaniu odwołania do zestawu za pomocą karty .NET okna dialogowego Dodaj Odwołanie, odwołanie wskazuje na pośrednie odwołanie do zestawu, który jest zestawem zawierającym wszystkie informacje o typie i podpisie, ale nie musi zawierać żadnego kodu. Karta .NET zawiera listę odwołań do zestawów, które odpowiadają zestawom środowiska uruchomieniowego w .NET Framework. Ponadto wyświetla listę odwołań do zestawów, które odpowiadają zestawom środowiska uruchomieniowego w zarejestrowanych folderach AssemblyFoldersEx używanych przez inne firmy.  
  
## <a name="multi-targeting"></a>Wielowersyjność kodu  
 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] pozwala na wybór wersji .NET Framework, która działa albo w Środowisku uruchomieniowym języka wspólnego (CLR) wersja 2 lub wersja 4. Dotyczy wersji .NET Framework 2.0, 3.0, 3.5, 4, 4.5 oraz 4.5.1 i wersji Silverlight 1.0, 2.0 i 3.0. Jeśli zostanie wydana nowa wersja .NET Framework oparta na wersji CLR 2.0 lub wersji 4, Framework może być zainstalowany przy użyciu odpowiedniego pakietu i automatycznie pojawi się jako cel w programie Visual Studio.  
  
## <a name="how-type-resolution-works"></a>Sposób, a jak działa typ rozwiązania  
 W czasie wykonywania CLR rozwiązuje typy w zestawie szukając w pamięci podręcznej GAC, katalogu bin i wszelkich ścieżkach sondowania. Jest to obsługiwane przez moduł ładujący fusion. Ale skąd moduł ładujący fusion wie czego szukać? To zależy od rozdzielczości wybranej w czasie projektowania, podczas kompilowania aplikacji.  
  
 Podczas kompilacji, kompilator rozwiązuje typy aplikacji używając zestawów odwołania. W .NET Framework w wersji 2.0, 3.0, 3.5, 4, 4.5 i 4.5.1, zestawy odwołania są instalowane podczas instalacji .NET Framework.  
  
 Zestawy odwołania są dostarczane przez pakiet docelowy, który jest dostarczany z odpowiednią wersją .NET Framework SDK. Framework sam w sobie dostarcza tylko zestawy środowiska uruchomieniowego. W celu skompilowania aplikacji należy zainstalować zarówno .NET Framework jak i odpowiadające mu .NET Framework SDK.  
  
 W przypadku elementem docelowym jest konkretny .NET Framework, system kompilacji rozpoznaje wszystkie typy używając zestawów odwołań w pakiecie docelowym. W czasie wykonywania moduł ładujący fusion rozpoznaje te same typy do zestawów środowiska uruchomieniowego, które z reguły są zlokalizowane w GAC.  
  
 Jeśli zestawy odwołań nie są dostępne, wtedy system kompilacji rozwiązuje typy zestawów używając zestawów środowiska uruchomieniowego. Ponieważ zestawy środowiska uruchomieniowego w GAC nie są rozpoznawane przez numer wersji pomocniczej, jest możliwe, że zostanie rozpoznany zły zestaw. Może się to zdarzyć gdy na przykład istnieje odwołanie do nowej metody wprowadzonej w .NET Framework w wersji 3.5 podczas gdy wersją docelową jest 3.0 Kompilacja zostanie wykonana pomyślnie, a aplikacja będzie działać na komputerze kompilacji, ale nie będzie działać na komputerze, na którym nie ma zainstalowanej wersji 3.5.  
  
 Pakiet docelowy, który jest teraz dostarczany z .NET Framework SDK zawiera listę wszystkich zestawów środowiska uruchomieniowego w danej wersji środowiska, nazywaną listą redystrybucji (redist). Uniemożliwia to systemowi kompilacji rozwiązanie typów w złej wersji zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)