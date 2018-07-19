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
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811924"
---
1. Jeśli planujesz wdrażanie aplikacji za pomocą narzędzia Web Deploy w programie Visual Studio, należy zainstalować najnowszą wersję narzędzia Web Deploy na serwerze.

    Aby zainstalować narzędzie Web Deploy, należy użyć [Instalatora platformy sieci Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Aby znaleźć link Instalatora platformy sieci Web za pomocą programu IIS, wybierz **IIS** w okienku po lewej stronie w Menedżerze serwera. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz pozycję **Internet Information Services (IIS) Manager**.)

    W oknie Instalatora platformy sieci Web możesz znaleźć narzędzia Web Deploy na karcie aplikacje. Możesz również uzyskać bezpośrednio z poziomu Instalatora [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Sprawdź, czy narzędzie Web Deploy działa poprawnie, otwierając **Panel sterowania > System i Zabezpieczenia > Narzędzia administracyjne > usługi** i upewnij się, że **Usługa agenta wdrażania sieci Web** działa ( Nazwa usługi jest inny w starszych wersjach).

    Jeśli nie jest uruchomiona usługa agenta, należy ją uruchomić. Jeśli nie ma go na wszystkich, przejdź do strony **Panel sterowania > programy > Odinstaluj program**, Znajdź **Microsoft Web Deploy <version>** . Możliwość **zmiany** instalacji i upewnij się, że wybierasz **zostanie zainstalowana na lokalnym dysku twardym** składników Web Deploy. Wykonaj kroki instalacji zmiany.