---
title: Hierarchiczna organizacja zasobów do lokalizacji
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c46fbfe13e7e4c795703a53debedca20ae39c145
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752323"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Hierarchiczna organizacja zasobów do lokalizacji

W programie Visual Studio zlokalizowanych zasobów (dane, takie jak parametry i obrazy odpowiednie do każdego kultury) są przechowywane w oddzielnych plików i załadować zgodnie z ustawieniem kultury interfejsu użytkownika. Aby zrozumieć, jak zlokalizowanych zasobów są ładowane, warto traktować ich jako zorganizowane hierarchicznie.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Typy zasobów w hierarchii

-   Zasoby rezerwowe dla Twojego domyślną kulturę, na przykład angielski ("en"), znajdują się na szczycie hierarchii. Te zasoby rezerwowe są jedynymi osobami, które nie mają własnych pliku. są one przechowywane w zestawie głównym.

-   Poniżej zasoby rezerwowe są zasoby dla dowolnej neutralne kultury. Określa kulturę neutralną jest skojarzony z językiem, ale nie kraj/region. Na przykład francuski (fr") to kultura neutralna. (Zasoby rezerwowe są również dla kultury neutralnej, ale wspaniałe).

-   Poniżej kultury neutralnej zasoby są zasoby dla dowolnej określonej kultury. Określoną kulturę jest skojarzony z język i kraj/region. Na przykład kanadyjskich francuski ("fr-CA") jest określoną kulturą.

 Jeśli aplikacja próbuje załadować żadnych zasobów zlokalizowanych, takiego jak ciąg i nie zostanie znaleziona, aż znajdzie plik zasobów zawierających żądanego zasobu będą przesyłane w hierarchii.

 Najlepszym sposobem na przechowywanie zasobów jest ich możliwie generalize. Oznacza to przechowywać zlokalizowanych ciągów, obrazy, itd w plików zasobów dla kultury neutralnej zamiast określone kultury, jeśli to możliwe. Na przykład jeśli zasoby dla belgijskiego francuski ("fr — można") kultury i bezpośrednio nad zasoby są zasoby rezerwowe w języku angielskim, problem może spowodować, gdy ktoś korzysta z aplikacji w systemie, skonfigurowane dla kultury francuskim kanadyjskich. System wyszukuje to zestaw satelicki "fr-CA", ale nie można go odnaleźć, więc ładuje główny zestaw zawierający zasoby rezerwowej, angielski, zamiast ładowanie zasobów francuskim. Na poniższej ilustracji przedstawiono w tym scenariuszu niepożądane.

 ![Tylko określonych zasobów](../ide/media/vbspecificresourcesonly.gif)

 Jeśli wykonujesz zalecaną praktyką umieszczenia jak najwięcej zasobów, jak to możliwe w pliku neutralnego zasobu dla kultury "fr" francuskim kanadyjskich będzie widoczny dla użytkownika nie zasoby oznaczone dla "fr — można" kultury, ale zostaną pokazane ciągów w języku francuskim. Następujących sytuacji przedstawiono w tym scenariuszu preferowany.

 ![NeutralSpecificResources — grafika](../ide/media/vbneutralspecificresources.gif)

## <a name="see-also"></a>Zobacz także

- [Neutralny język zasobów do lokalizacji](../ide/neutral-resources-languages-for-localization.md)
- [Zabezpieczenia a zlokalizowane zestawy satelickie](../ide/security-and-localized-satellite-assemblies.md)
- [Lokalizowanie aplikacji](../ide/localizing-applications.md)
- [Globalizacja i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md)