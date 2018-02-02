---
title: "Obciążenie nauki dane i aplikacje analityczne w programie Visual Studio | Dokumentacja firmy Microsoft"
description: "Obciążenie nauki dane i aplikacje analityczne w programie Visual Studio łączy Python, R, F # i ich dystrybucje odpowiednich środowiska uruchomieniowego tym Anaconda."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
- devlang-python
- devlang-fsharp
ms.tgt_pltfrm: 
ms.topic: landing-page
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: a5ebd00d2eac1b6f8a88a6c3510e822a5eed6734
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="data-science-and-analytical-applications-workload"></a>Obciążenie nauki dane i aplikacje analitycznych

Obciążenie nauki dane i aplikacje analitycznych, wybierz i zainstaluj przez Instalator programu Visual Studio, połączono trzech językach i dystrybucji ich odpowiednich środowiska uruchomieniowego:

- [R i klienta Microsoft R](../rtvs/index.md)
- [Python i Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F # w środowisku .NET Framework](/dotnet/fsharp/)

![Obciążenie nauki danych i analizy aplikacji w Instalatorze programu Visual Studio](media/data-science-workload.png)

R i Python są dwa podstawowe języków skryptowych używany do analizy danych. Zarówno języki są łatwe dowiedzieć się więcej i są obsługiwane przez rozbudowany ekosystem pakietów. Te pakiety adresów szeroką gamę scenariuszy, takich jak uzyskiwanie danych, czyszczenie uczenia modelu, wdrożenia i kreślenia. F # jest również zaawansowane języka .NET funkcjonalny, który jest odpowiedni dla różnych zadań przetwarzania danych.

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu programu Visual Studio z R, Python i F #](media/data-science-workload-screens.png)](media/data-science-workload-screens.png)

## <a name="workload-options"></a>Opcje obciążenia

Domyślnie obciążenie instalowane są następujące opcje, które można modyfikować w sekcji podsumowania dla obciążeń w Instalatorze programu Visual Studio:

- Obsługa języka F #
- Python:
  - Obsługa języka Python
  - [Anaconda3 64-bitowych](https://www.continuum.io) (A Python distro biblioteki nauki dużą ilością danych i interpreter języka Python)
  - Obsługa sieci web języka Python
  - - Obsługa szablonów Cookiecutter
- R:
  - Obsługa języków R
  - Obsługa środowiska uruchomieniowego dla narzędzi programistycznych R
  - [Klient Microsoft R](/machine-learning-server/r-client/what-is-microsoft-r-client) (firmy Microsoft w pełni zgodne, obsługiwane społeczności R interpreter z bibliotekami ScaleR do szybsze obliczeń na pojedynczych węzłów lub klastry. Można również użyć dowolnego języka R z [sieci CRAN](https://cran.r-project.org/).)

Chociaż F # jest uwzględniona w wielu innych obciążeń i Python ma własną obciążenie, nauki dane i aplikacje analitycznych jest tylko obciążenia w chwili obecnej, która obejmuje R. Jednakże można także zainstalować R niezależnie od obciążenia. Na **pojedynczych składników** w Instalatorze, a następnie wybierz następujące opcje R:

- **Programowanie działań > Obsługa języka R**
- **Programowanie działań > Microsoft R klienta**
- **Kompilatory, kompilacji narzędzia i środowisk uruchomieniowych > Obsługa środowiska uruchomieniowego dla narzędzi programistycznych R**

## <a name="sql-server-integration"></a>Integracja programu SQL Server

Obsługa programu SQL Server przy użyciu zarówno R i Python przeprowadzić zaawansowane metody analizy bezpośrednio w programie SQL Server. Obsługa języka R jest dołączana do programu SQL Server 2016 lub nowszy; Obsługa języka Python jest dostępne w programie SQL Server 2017 CTP 2.0 lub nowszy.

Uruchamiając kodu, w którym mieszka już danych użytkownik korzysta z ma następujące zalety:

- **Eliminacja przenoszenia danych**: zamiast przenoszenia danych z bazy danych do aplikacji lub modelu, można tworzyć aplikacje R i Python w bazie danych. Ta funkcja eliminuje bariery zabezpieczeń, zgodności ładu, integralności i hostem podobne zagadnienia związane z przenoszenia dużych ilości danych wokół. Można również korzystać z zestawów danych, który nie mieści się w pamięci komputera klienta.

- **Łatwe wdrażanie**: gdy masz R lub Python modelu gotowe, jego wdrożeniem w środowisku produkcyjnym polega na osadzenia go w skrypcie T-SQL. Dowolnej aplikacji klienta SQL, w dowolnym języku mogą następnie korzystać z modelami i analizy poprzez wywołanie procedury składowanej. Nie określonego integracji R lub Python są niezbędne.

- **Korporacyjnej wydajności i skalowania**: jak w pamięci tabel i kolumn przechowywania indeksów z interfejsami API skalowalnej wysokowydajnej w pakietach RevoScaleR i RevoScalePy, można użyć zaawansowanych możliwości programu SQL Server. Eliminacja przenoszenia danych również oznacza, że należy unikać ograniczenia pamięci klienta wraz z rozwojem danych lub chcesz zwiększyć wydajność aplikacji.

- **Rozszerzalność sformatowanego**: można zainstalować i uruchomić dowolne z najnowszą typu open source R lub Python pakietów w programie SQL Server Tworzenie bezpośrednich uczenie i aplikacje AI na dużych ilości danych w programie SQL Server. Instalowanie pakietu w programie SQL Server jest tak proste, jak instalowanie pakietu na komputerze lokalnym.

- **Międzynarodowe dostępność bez ponoszenia dodatkowych kosztów**: R i Python integracji są dostępne we wszystkich wersjach programu SQL Server 2017 i później, w tym wersja Express. (Obsługa języka R jest dostępne w programie SQL Server 2016 lub nowszy).

Aby w pełni korzystać z integracji programu SQL Server, użyj Instalatora programu Visual Studio do zainstalowania **magazynu danych i przetwarzania** obciążenie z **SQL Server Data Tools** opcji. Tę druga opcję umożliwia SQL IntelliSense, wyróżnianie składni i wdrożenia.

![Obciążenie przechowywania i przetwarzania danych](media/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Magazyn danych i opcje obciążenie przetwarzania](media/data-storage-workload-options.png)

Informacje dodatkowe:

- [Praca z programu SQL Server i R](../rtvs/sql-server.md)
- [W bazie danych Advanced Analytics z języka R w programie SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [Python w 2017 serwera SQL: enhanced uczenia maszynowego w bazie danych (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Dodatkowe usługi i zestawy SDK

Oprócz co to jest pracą nauki danych i analizy aplikacji bezpośrednio usługa Azure, komputery przenośne i zestawu Azure SDK dla języka Python także są przydatne do analizy danych.

Zestaw Azure SDK for Python ułatwia zużywają i zarządzania usługami Microsoft Azure z aplikacji działających w systemie Windows, Mac i Linux. Aby uzyskać więcej informacji, zobacz [zestawu Azure SDK dla języka Python](../python/azure-sdk-for-python.md)

Azure notesów (obecnie w wersji zapoznawczej) umożliwia wolnego online dostęp do notesów Jupyter działającą w chmurze Microsoft Azure. Usługa obejmuje notesów próbki w języku Python, R i F # ułatwiających rozpoczęcie pracy. Visit[notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu Azure notesów wraz z wprowadzeniem do R próbki](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png)