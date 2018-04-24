---
title: Często zadawane pytania dotyczące debugowania migawki | Dokumentacja firmy Microsoft
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8547c14cfd8a59d775c909edb06e3542b18710c8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Często zadawane pytania dla migawki debugowania w programie Visual Studio

Oto lista zagadnień, które może być znaleziona podczas debugowania aplikacji platformy Azure na żywo za pomocą debugera migawki.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Jaki jest koszt wydajności migawki?

Gdy debuger migawki przechwytuje migawki aplikacji, jest rozwidlania procesu aplikacji i zawieszania rozwidlonych kopiowania. Podczas debugowania migawki są debugujesz rozwidlonych kopię procesu. Ten proces tylko 10-20 milisekund, ale nie kopiuje pełnego stosu aplikacji; Zamiast tego kopiuje tabeli strony i ustawia stron kopię zapisu. Jeśli niektóre obiekty aplikacji w przypadku zmiany sterty ich odpowiednich strony są kopiowane. Każda migawka w związku z tym ma bardzo małych koszt w pamięci (rzędu setki kilobajtów dla większości aplikacji). 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Co się dzieje w przypadku usługi aplikacji Azure skalowalnych w poziomie (wiele wystąpień Moja aplikacja)?

Jeśli masz wiele wystąpień aplikacji snappoints zastosowane do każdego pojedynczego wystąpienia. Tylko pierwszy snappoint trafienie warunkom określonym tworzy migawkę. Jeśli masz wiele snappoints kolejnych migawek pochodzić z tego samego wystąpienia, utworzony pierwszej migawki. Logpoints wysyłane do okna wyjściowego będzie wyświetlana tylko komunikaty z jednego wystąpienia, gdy logpoints wysyłane do dzienników aplikacji wysyłania komunikatów z każde wystąpienie. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Jak debugera migawki Załaduj symbole?

Debuger migawki wymaga, aby mieć zgodnych symboli dla aplikacji albo lokalnie, i wdrożony w usłudze aplikacji Azure (osadzone pliki PDB obecnie nie są obsługiwane). Debuger migawki automatycznie pobiera symbole z usługi aplikacji Azure. Począwszy od programu Visual Studio 2017 wersji 15,2, wdrażając w usłudze aplikacji Azure również wdraża symboli aplikacji.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Debuger migawki działa z kompilacjami wydania mojej aplikacji?

Tak — debuger migawki jest przeznaczony do pracy z kompilacjami wydania. Gdy snappoint znajduje się w funkcji, funkcja jest ponownie kompilowana wersji debugowania, dzięki czemu możliwością debugowania. Po zatrzymaniu debugera migawki, te funkcje są zwracane do ich kompilacji wydania. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Logpoints mogą powodować efekty uboczne mojej aplikacji w środowisku produkcyjnym?

Nie - komunikaty dziennika, należy dodać do aplikacji są oceniane praktycznie. Nie można ich spowodować żadnych efektów ubocznych aplikacji. Jednak niektóre właściwości natywnej nie mogą być dostępne z logpoints. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Debuger migawki działa, jeśli serwer jest obciążony?

Tak, debugowanie migawki można pracować na serwerach w ramach obciążenia. Debuger migawki ogranicza i nie przechwytywania migawek w sytuacjach, w której jest mała ilość wolnej pamięci na serwerze.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Jak odinstalować debugera migawki?

Można odinstalować rozszerzenia lokacji debugera migawki w usłudze App Service z następujących kroków:

1. Wyłącz w usłudze App Service za pośrednictwem Eksplorator chmury w programie Visual Studio lub w portalu Azure.
1. Przejdź do witryny Kudu w usłudze App Service (to znaczy yourappservice. **Menedżer sterowania usługami**. azurewebsites.net) i przejdź do **lokacji rozszerzenia**.
1. Kliknij przycisk X w rozszerzeniu lokacji debugera migawki go usunąć.

## <a name="see-also"></a>Zobacz także

[Debugowanie w programie Visual Studio](../debugger/index.md)  
[Debugowania na żywo aplikacji ASP.NET, za pomocą debugera migawki](../debugger/debug-live-azure-applications.md)  
[Rozwiązywanie problemów i znane problemy dotyczące debugowania migawki](../debugger/debug-live-azure-apps-troubleshooting.md)
