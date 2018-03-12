---
title: "Zarządzanie odwołaniami w projekcie w programie Visual Studio for Mac | Dokumentacja firmy Microsoft"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 99f3ba9e5192bc17df23a93c9cad7e953797e9b4
ms.sourcegitcommit: 3285243d6c0521266053340fe06505885d12178b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2018
---
# <a name="managing-references-in-a-project"></a>Zarządzanie odwołaniami w projekcie

Program Visual Studio dla komputerów Mac udostępnia dwa sposoby Dodawanie dodatkowych odwołań do projektu:

![Odwołania do projektu](media/projects-and-solutions-image10.png)

Są to:

* Odwołania
* NuGets (dodanej za pomocą folderu pakietów)

Ponadto odwołania sieci Web i odwołania do natywnej można również dodać do każdego projektu.

## <a name="assembly-references"></a>Odwołania do zestawów

Każdy framework w Xamarin jest dostarczany z ponad dwanaście zestawy. Nie wszystkie te pakiety zestawu odwołuje się do projektu domyślnego. 

Aby edytować pakiety, które odwołują się do projektu, należy użyć _odwołania Edytuj_ okno dialogowe, które mogą być wyświetlane przez dwukrotne kliknięcie odwołuje się do folderu lub wybierz Edytuj odwołania na swoich działań menu kontekstowe:

![Okno dialogowe odwołania do zestawu](media/projects-and-solutions-image11.png)

Informacji na temat zestawów dostępnych dla każdej platformy Xamarin, można znaleźć w [dostępne zestawy](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) przewodnik.

## <a name="nuget"></a>NuGet

NuGet jest najbardziej popularnych Menedżer pakietów dla rozwoju platformy .NET. Visual Studio do obsługi NuGet dla komputerów Mac umożliwia wyszukiwanie pakiety do dodania do projektu.

Aby to zrobić, kliknij prawym przyciskiem myszy **pakietu** folderu w konsoli do rozwiązania, a następnie wybierz opcję Dodaj pakiety.

Podano więcej informacji na temat używania pakietu NuGet w [pakietu w tym NuGet w projekcie](~/nuget-walkthrough.md) wskazówki.
