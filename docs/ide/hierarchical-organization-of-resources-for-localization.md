---
title: "Hierarchiczna organizacja zasobów do lokalizacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f52d57d45c0f78a5bd64b16f10c9bb7c2256cd7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Hierarchiczna organizacja zasobów do lokalizacji
W programie Visual Studio zlokalizowanych zasobów (dane, takie jak parametry i obrazy odpowiednie do każdego kultury) są przechowywane w oddzielnych plików i załadować zgodnie z ustawieniem kultury interfejsu użytkownika. Aby zrozumieć, jak zlokalizowanych zasobów są ładowane, warto traktować ich jako zorganizowane hierarchicznie.  
  
## <a name="kinds-of-resources-in-the-hierarchy"></a>Typy zasobów w hierarchii  
  
-   W górnej części hierarchii znajdują się zasoby ostatecznej rezerwy dla Twojego domyślną kulturę, na przykład angielski ("en"). Są to jedyne zasoby, które nie mają własnych pliku. są one przechowywane w zestawie głównym.  
  
-   Poniżej zasoby rezerwowe są zasoby dla dowolnej neutralne kultury. Określa kulturę neutralną jest skojarzony z językiem, ale nie kraj/region. Na przykład francuski (fr") to kultura neutralna. (Należy pamiętać, że zasoby rezerwowe są również dla kultury neutralnej, ale wspaniałe.)  
  
-   Poniżej te są zasoby dla dowolnej określonej kultury. Określoną kulturę jest skojarzony z język i kraj/region. Na przykład kanadyjskich francuski ("fr-CA") jest określoną kulturą.  
  
 Jeśli aplikacja próbuje załadować żadnych zasobów zlokalizowanych, takiego jak ciąg i nie zostanie znaleziona, aż znajdzie plik zasobów zawierających żądanego zasobu będą przesyłane w hierarchii.  
  
 Najlepszym sposobem na przechowywanie zasobów jest ich możliwie generalize. Oznacza to przechowywać zlokalizowanych ciągów, obrazy, itd w plików zasobów dla kultury neutralnej zamiast określone kultury, jeśli to możliwe. Na przykład jeśli zasoby dla belgijskiego francuski ("fr — można") kultury i bezpośrednio nad zasoby są zasoby rezerwowe w języku angielskim, problem może spowodować, gdy ktoś korzysta z aplikacji w systemie, skonfigurowane dla kultury francuskim kanadyjskich. System będzie Wyszukaj to zestaw satelicki "fr-CA", nie ją znaleźć i załadować główny zestaw zawierający rezerwowy zasób, który jest angielski, zamiast ładowanie zasobów francuskim. Na poniższej ilustracji przedstawiono w tym scenariuszu niepożądane.  
  
 ![Tylko określonych zasobów](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")  
  
 Jeśli wykonujesz zalecaną praktyką umieszczenia jak najwięcej zasobów, jak to możliwe w pliku neutralnego zasobu dla kultury "fr" francuskim kanadyjskich będzie widoczny dla użytkownika nie zasoby oznaczone dla "fr — można" kultury, ale czy zostaną pokazane ciągów w języku francuskim. Następujących sytuacji przedstawiono w tym scenariuszu preferowany.  
  
 ![NeutralSpecificResources — grafika](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")  
  
## <a name="see-also"></a>Zobacz też  
 [Neutralny język zasobów do lokalizacji](../ide/neutral-resources-languages-for-localization.md)   
 [Zabezpieczenia a zlokalizowane zestawy satelickie](../ide/security-and-localized-satellite-assemblies.md)   
 [Lokalizowanie aplikacji](../ide/localizing-applications.md)   
 [Globalizacja i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md)   
 [Porady: ustawienie kultury i kultury interfejsu użytkownika dla globalizacja formularzy systemu Windows](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)   
 [Porady: ustawienie kultury i kultury interfejsu użytkownika dla globalizacji strony sieci Web ASP.NET](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0)