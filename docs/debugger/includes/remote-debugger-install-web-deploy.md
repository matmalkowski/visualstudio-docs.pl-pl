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
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
1. Jeśli zamierzasz wdrożyć aplikacji z narzędzia Web Deploy w programie Visual Studio, należy zainstalować najnowszą wersję narzędzia Web Deploy na serwerze.

    Aby zainstalować narzędzie Web Deploy, użyj [Instalatora platformy sieci Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Aby znaleźć łącza Instalatora platformy sieci Web za pomocą programu IIS, wybierz **IIS** w lewym okienku w Menedżerze serwera. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz **Internet Information Services (IIS) Manager**.)

    W Instalatorze platformy sieci Web możesz znaleźć narzędzia Web Deploy na karcie aplikacje. Możesz również uzyskać Instalator bezpośrednio z [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Sprawdź, czy narzędzie Web Deploy działa poprawnie, otwierając **Panel sterowania > System i Zabezpieczenia > Narzędzia administracyjne > usługi** i upewnij się, że **Usługa agenta sieci Web wdrożenia** działa ( Nazwa usługi jest inny w starszych wersjach).

    Jeśli usługa agenta nie jest uruchomiona, uruchom ją. Jeśli nie ma go na wszystkich, przejdź do **Panel sterowania > programy > Odinstaluj program**, Znajdź **Microsoft Web Deploy <version>** . Wybierz **zmiany** instalacji i upewnij się, że wybierasz **zostanie zainstalowana na lokalnym dysku twardym** składników Web Deploy. Wykonaj kroki instalacji zmiany.