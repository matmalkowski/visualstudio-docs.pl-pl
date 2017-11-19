---
redirect_url: shell/servicing-guidelines-for-isolated-shell-applications
title: "Wytyczne dotyczące obsługi izolowanych powłoki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e15d228794fb03441d42c081f11bf75b11fdd45
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Obsługa wytycznych dla aplikacji Isolated Shell
Podczas dystrybucji aplikacji powłoki programu Visual Studio izolowane musi być udostępnienia aktualizacji oprogramowania dla aplikacji po jej zainstalowaniu. Aby to zrobić, należy zainstalować aplikację przy użyciu pliku Instalatora Microsoft Windows (MSI). Tego rodzaju instalacji umożliwia aktualizacji oprogramowania firmy Microsoft, aby być przenoszony przez sieci Web pobierania i używane przez klientów bez konieczności interwencji niestandardowych.  
  
## <a name="servicing-requirements"></a>Wymagania dotyczące obsługi  
 Można zapewnić, że instalację programu isolated shell można zezwolić na aktualizacje upewniając się, że program instalacyjny spełnia następujące kryteria trzy.  
  
### <a name="redistribute-by-using-an-msi"></a>Ponowna dystrybucja za pomocą Instalatora MSI  
 Aby wykonać ponowną dystrybucję aplikacji, należy użyć Instalatora MSI, ponieważ Instalator MSI zachowuje tożsamości produktu i upewnij się, że aplikacja ma lokalizacji fizycznej na komputerze klienckim. Moduły scalania (pliki .msm) nie zapewniają takich gwarancji i nie powinna być używana.  
  
### <a name="accounting-for-custom-actions"></a>Dla akcji niestandardowych  
 Akcje niestandardowe są dyrektywy niestandardowej instalacji programu Instalatora. Akcje niestandardowe Zmień parametry, takie jak lokalizacje plików, ustawień rejestru, ustawienia użytkownika lub inne elementy wymagane do instalacji. Akcje niestandardowe może manipulować danymi w czasie instalacji.  
  
 Użycie akcje niestandardowe w programie instalacyjnym, upewnij się, że akcji niestandardowej co godzinę instalacji muszą mieć odpowiednich akcji niestandardowych można cofnąć, gdy użytkownik odinstaluje aplikację. Program instalacyjny nie podaj odpowiednie odinstalować akcji niestandardowej, usunięcie aplikacji spowoduje zamknięcie go częściowo zainstalowane.  
  
-   Akcji niestandardowej, która opiera się na określonej wersji pliku lub skrót wartości zakończy się niepowodzeniem, gdy aktualizacje oprogramowania zmienić te wersje lub wartości mieszania. W takim przypadku akcji niestandardowej, należy ręcznie zaktualizować te wartości. Dodatkowe problem występuje, jeśli wersje pliku lub skrót wartości są wspólne dla wersji produktu. Unikaj tę zależność, jeśli to możliwe.  
  
### <a name="accounting-for-shared-files"></a>Dla udostępnionych plików  
 Udostępnione pliki o takich samych nazwach i są zainstalowane w tej samej lokalizacji przez wiele produktów. Produkty te mogą się różnić w wersji lub giełdowych utrzymywanie jednostki SKU i produkty mogą współistnieć na danym komputerze. Jednak udostępnione pliki utworzyć obsługi problemów z kilku powodów:  
  
-   Aktualizowanie udostępnionych plików może spowodować problemy ze zgodnością aplikacji, ponieważ aktualizacja do jednej aplikacji mogą ulec zmianie wersji pliku używany przez aplikację drugiej, który nie został zaktualizowany. Pliki instalacyjne dla produktów współdzielące pliki liczba odwołań do udostępnionych plików. W związku z tym odinstalowywanie produktu nie wpływa na udostępnionych plików poza zmniejszanie liczba zainstalowanych wystąpień.  
  
-   Instalator Quick Fix Engineering (QFE) zostanie przywrócona do wersji produktów, które Instalator QFE obsługiwanych wersji plików. Ten proces potencjalnie dzieli aplikację, która dostarczył zaktualizowanego pliku udostępnionego.