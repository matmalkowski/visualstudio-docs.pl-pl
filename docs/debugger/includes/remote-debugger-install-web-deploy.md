---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 2d82fc0eb60b2680be9ed2bdb7de13313593da0d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
1. Jeśli zamierzasz wdrożyć aplikacji z narzędzia Web Deploy w programie Visual Studio, należy zainstalować najnowszą wersję narzędzia Web Deploy na serwerze.

    Aby zainstalować narzędzie Web Deploy, użyj [Instalatora platformy sieci Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx) lub uzyskać Instalatora bezpośrednio z [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). Na karcie aplikacji można znaleźć narzędzia Web Deploy. 

2. Sprawdź, czy narzędzie Web Deploy działa poprawnie, otwierając **Panel sterowania > System i Zabezpieczenia > Narzędzia administracyjne > usługi** i upewnij się, że **Usługa agenta sieci Web wdrożenia** działa ( Nazwa usługi jest inny w starszych wersjach).

    Jeśli usługa agenta nie jest uruchomiona, uruchom ją. Jeśli nie ma go na wszystkich, przejdź do **Panel sterowania > programy > Odinstaluj program**, Znajdź **Microsoft Web Deploy <version> **. Wybierz **zmiany** instalacji i upewnij się, że wybierasz **zostanie zainstalowana na lokalnym dysku twardym** składników Web Deploy. Wykonaj kroki instalacji zmiany.