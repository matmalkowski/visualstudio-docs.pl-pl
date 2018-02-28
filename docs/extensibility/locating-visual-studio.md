---
title: Lokalizowanie programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 08/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5623ea382266fdbcd59bbe57b71522a7a1f4a31e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="locating-visual-studio"></a>Lokalizowanie programu Visual Studio

Począwszy od programu Visual Studio 2017 r, można zainstalować wiele wystąpień tej samej wersji lub nawet edition. Jest to przydatne, jeśli chcesz wyświetlić podgląd nowych funkcji na komputerze deweloperskim głównej przy zachowaniu poprzedniej instalacji. Ze względu na te zmiany nie istnieje jednym środowisku zmiennej lub rejestru wartość używanych w celu zlokalizowania wystąpienia. Zamiast tego można użyć [COM zapytania interfejsu API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) znaleźć wystąpień na podstawie kryteriów odpowiednie do rozszerzenia.

Jest to interfejs API szybkie, tylko do odczytu z pakietami NuGet, które są dostępne dla kodu natywnego i zarządzanego.

| Kod | Package |
| ---- | --- |
| Natywny | https://nuget.org/Packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Zarządzane | https://nuget.org/Packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Zlokalizuj pojedynczego wystąpienia daną ścieżkę lub bieżącego procesu lub wyliczyć wszystkie wystąpienia. Zobacz [nasze przykłady](https://github.com/Microsoft/vs-setup-samples) pełną przykłady można znaleźć programu Visual Studio.

## <a name="tools"></a>Narzędzia

Aby znaleźć Visual Studio i innych narzędzi w środowiska kompilacji, skrypty programu PowerShell, pliki instalacyjne i scenariuszy, mamy kilka narzędzi typu open source, można użyć bezpośrednio lub ponownej dystrybucji wraz z własnych skryptów.

| Projekt | Opis |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Natywny jednego pliku wykonywalnego można znaleźć wystąpień spełniających kryteria, takich jak wersji lub wersji wstępnej, jakie produkt jest zainstalowany i obciążeń, które są zainstalowane. Obsługuje również wyszukiwanie programu Visual Studio 2010 i nowszych, ale mniej informacje są zwracane, które dla programu Visual Studio 2017 i nowszych. Zobacz [wiki](https://github.com/Microsoft/vswhere/wiki) przykłady. |
| [Polecenia cmdlet VSSetup](https://github.com/Microsoft/vssetup.powershell) | Obsługiwane polecenia cmdlet programu PowerShell 2.0 lub nowszej, które zwracają informacje sformatowanego jako obiekty można znaleźć wystąpień, w oparciu o te same kryteria jak _vswhere_ i aby dowiedzieć się więcej właściwości o wystąpieniach. Zobacz [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) przykłady. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Automatycznie lokalizuje _VSIXInstaller_ i przekazuje za pomocą wiersza polecenia do zainstalowania _*.vsix_ pliku. Może to być przydatne w pliki instalacyjne, które nie mają bezpośredniego Obsługa zapytań interfejsów API. Zobacz [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) przykłady. |

## <a name="see-also"></a>Zobacz też

* [Zmiany Instalatora 2017 programu Visual Studio](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
