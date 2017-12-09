---
title: "Dane nauki i obciążenia aplikacji analityczne w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
- devlang-python
- devlang-fsharp
ms.tgt_pltfrm: 
ms.topic: landing-page
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 5e7738d03fa0c9b8b460fe1b2fb4bc17076fa3b5
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="data-science-and-analytical-applications-workload"></a>Obciążenie nauki dane i aplikacje analitycznych

Obciążenie nauki dane i aplikacje analityczne w programie Visual Studio, połączono trzech językach i dystrybucji ich odpowiednich środowiska uruchomieniowego:

- [R i klienta Microsoft R](../rtvs/index.md)
- [Python i Anaconda](../python/python-in-visual-studio.md)
- [F # w środowisku .NET Framework](https://docs.microsoft.com/dotnet/fsharp/)

![Obciążenie nauki danych i analizy aplikacji w Instalatorze programu Visual Studio](media/data-science-workload.png)

R i Python są dwa podstawowe języków skryptowych używany do analizy danych. Zarówno języki są łatwe dowiedzieć się więcej i są obsługiwane przez rozbudowany ekosystem pakietów. Te pakiety adresów szeroką gamę scenariuszy, takich jak uzyskiwanie danych, czyszczenie uczenia modelu, wdrożenia i kreślenia. I F # to zaawansowane języka .NET funkcjonalny, który jest odpowiedni dla różnych zadań przetwarzania danych.

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu programu Visual Studio z R, Python i F #](media/data-science-workload-screens.png)](media/data-science-workload-screens.png)

## <a name="workload-options"></a>Opcje obciążenia

Domyślnie obciążenie instalowane są następujące opcje, które można modyfikować w sekcji podsumowania dla obciążeń w Instalatorze programu Visual Studio:

- Obsługa języka F #
- Python:
  - Obsługa języka Python
  - Obsługa sieci web języka Python
  - [Anaconda3 64-bitowych](https://www.continuum.io) (A Python distro biblioteki nauki dużą ilością danych i interpreter języka Python)
  - Obsługa szablonów Cookiecutter
- R:
  - Obsługa języków R
  - [Klient Microsoft R](/machine-learning-server/r-client/what-is-microsoft-r-client) (firmy Microsoft w pełni zgodne, obsługiwane społeczności R interpreter z bibliotekami ScaleR do szybsze obliczeń na pojedynczych węzłów lub klastry. Można również użyć dowolnego języka R z [sieci CRAN](https://cran.r-project.org/).)
  - Obsługa środowiska uruchomieniowego dla narzędzi programistycznych R

Mimo że F # jest uwzględniona w wielu innych obciążeń i Python ma obciążenie własną, analizy danych analitycznych aplikacji jest obciążenie tylko w chwili obecnej, która obejmuje R. niezależnie od obciążenia, trzech składników R są również w  **Poszczególne składniki** kartę w Instalatorze. Wybierz opcje **rozwoju > Obsługa języków R**, **rozwoju > Microsoft R klienta**, i **kompilatorów kompilacji narzędzia i środowisk uruchomieniowych > Obsługa środowiska uruchomieniowego dla narzędzia deweloperskie R**.

## <a name="sql-server-integration"></a>Integracja programu SQL Server

Obsługa programu SQL Server przy użyciu zarówno R i Python przeprowadzić zaawansowane metody analizy bezpośrednio w programie SQL Server. Obsługa języka R jest dołączana do programu SQL Server 2016 lub nowszy; Obsługa języka Python jest dostępne w programie SQL Server 2017 CTP 2.0 lub nowszy.

Uruchamiając kodu, w którym mieszka już dane, korzysta się z kilku powodów:

- **Eliminacja przenoszenia danych**: zamiast przenoszenia danych z bazy danych do aplikacji lub modelu, można tworzyć aplikacje R i Python w bazie danych. Ta funkcja eliminuje bariery zabezpieczeń, zgodności ładu, integralności i hostem podobne zagadnienia związane z przenoszenia dużych ilości danych wokół. Umożliwia także korzystanie z zestawów danych, który nie mieści się w pamięci komputera klienta.

- **Łatwe wdrażanie**: gdy masz R lub Python modelu gotowe, jego wdrożeniem w środowisku produkcyjnym oznacza po prostu osadzanie w skrypcie T-SQL. Dowolnej aplikacji klienta SQL, w dowolnym języku mogą następnie korzystać z modelami i analizy poprzez wywołanie procedury składowanej. Nie określonego integracji R lub Python są niezbędne.

- **Korporacyjnej wydajności i skalowania**: jak w pamięci tabel i kolumn przechowywania indeksów z interfejsami API skalowalnej wysokowydajnej w pakietach RevoScaleR i RevoScalePy, można użyć zaawansowanych możliwości programu SQL Server. Eliminacja przenoszenia danych również oznacza, że należy unikać ograniczenia pamięci klienta wraz z rozwojem danych lub chcesz zwiększyć wydajność aplikacji.

- **Rozszerzalność sformatowanego**: można zainstalować i uruchomić dowolne z najnowszą typu open source R lub Python pakietów w programie SQL Server Tworzenie bezpośrednich uczenie i aplikacje AI na dużych ilości danych w programie SQL Server. Instalowanie pakietu w programie SQL Server jest tak proste, jak instalowanie pakietu na komputerze lokalnym.

- **Międzynarodowe dostępność bez ponoszenia dodatkowych kosztów**: R i Python integracji są dostępne we wszystkich wersjach programu SQL Server 2017 i później, w tym wersja Express. (Obsługa języka R jest dostępne w programie SQL Server 2016 lub nowszy).

Aby w pełni korzystać z integracji programu SQL Server, należy również zainstalować **magazynu danych i przetwarzania** obciążenie z **SQL Server Data Tools** opcji. Ta opcja umożliwia SQL IntelliSense, wyróżnianie składni i wdrożenia.

![Obciążenie przechowywania i przetwarzania danych](media/data-storage-workload.png) &nbsp;&nbsp; &nbsp;&nbsp; ![Magazyn danych i opcje obciążenie przetwarzania](media/data-storage-workload-options.png)

Informacje dodatkowe:

- [Praca z programu SQL Server i R](../rtvs/sql-server.md)
- [Zaawansowana analityka z języka R w programie SQL Server 2016 bazy](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [Python w 2017 serwera SQL: enhanced uczenia maszynowego w bazie danych](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Dodatkowe usługi i zestawy SDK

Oprócz co to jest pracą nauki danych i analizy aplikacji bezpośrednio usługa Azure, komputery przenośne i zestawu Azure SDK dla języka Python także są przydatne do analizy danych.

Zestaw Azure SDK for Python ułatwia zużywają i zarządzania usługami Microsoft Azure z aplikacji działających w systemach Windows, Mac OS x i Linux. Aby uzyskać więcej informacji, zobacz [zestawu Azure SDK dla języka Python](../python/azure-sdk-for-python.md)

Azure notesów (obecnie w wersji zapoznawczej) umożliwia wolnego online dostęp do notesów Jupyter działającą w chmurze Microsoft Azure. Usługa obejmuje notesów próbki w języku Python, R i F # ułatwiających rozpoczęcie pracy. Odwiedź stronę[notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu Azure notesów wraz z wprowadzeniem do R próbki](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png)