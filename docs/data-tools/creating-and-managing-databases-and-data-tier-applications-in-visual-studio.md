---
title: Projekty bazy danych, projekty z serwera i DAC projektów w programie Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ca08103614989ddbfd096a08a1531e756c9f67c
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176107"
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Projekty baz danych i aplikacji warstwy danych w programie Visual Studio

Projekty baz danych można użyć do tworzenia nowych baz danych, nowe aplikacje warstwy danych (DAC) i aktualizowanie istniejących baz danych i aplikacji warstwy danych. Projekty bazy danych i projektami DAC umożliwiają zastosowanie technik zarządzania projekt i kontroli wersji do swoich wysiłków programistycznych bazy danych w podobny sposób zastosowania tych technik do kodu zarządzanego lub natywnego. Możesz pomóc zespołowi zarządzania zmianami z bazami danych i serwery baz danych przez tworzenie projektu aplikacji DAC, projekt bazy danych lub server project i umieszczenie go w systemie kontroli wersji. Członkowie zespołu mogą następnie wyewidencjonowywanie plików do wprowadzić, tworzenie i testowanie zmian w środowisko programistyczne izolowanej lub piaskownicy, przed udostępnieniem ich zespołowi. Aby zapewnić jakość kodu, Twój zespół może zakończenie i przetestowanie wszystkich zmian dla konkretnej wersji bazy danych w środowisku przejściowym, przed wdrożeniem zmian w środowisku produkcyjnym.

Aby uzyskać listę funkcji bazy danych, które są obsługiwane przez aplikacje warstwy danych, zobacz [funkcje obsługiwane w aplikacji warstwy danych](/previous-versions/visualstudio/visual-studio-2010/ee362013(v=vs.100)). Jeśli korzystasz z funkcji w bazie danych, które nie są obsługiwane przez aplikacje warstwy danych, należy zamiast tego użyć projektu bazy danych, zarządzanie zmianami z bazą danych.

## <a name="common-high-level-tasks"></a>Typowe zadania wysokiego poziomu

|Ogólne zadania|Zawartość pomocnicza|
|----------------------|------------------------|
|**Rozpocznij tworzenie aplikacji warstwy danych:** DAC to nowe pojęcie wprowadzone w programie [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] zawierający definicję [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych i towarzyszące wystąpienia obiektów, które są używane przez serwer do klienta lub 3-warstwowej aplikacja. Aplikacji DAC programu zawiera obiekty bazy danych, takich jak tabele i widoki, wraz z wystąpienia jednostki, takie jak nazwy logowania. Używasz programu Visual Studio Utwórz projekt aplikacji DAC, tworzenie pliku pakietu aplikacji DAC i wysyłać ten plik pakietu aplikacji DAC administrator bazy danych w celu wdrożenia na wystąpienie [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] aparatu bazy danych.|-   [Tworzenie i zarządzanie nimi aplikacji warstwy danych](http://go.microsoft.com/fwlink/?LinkId=160741)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Wykonywanie programowanie iteracyjne bazy danych:** Jeśli jesteś deweloperem lub tester, zapoznaj się z części projektu, a następnie zaktualizuj je w środowisku izolowanym rozwoju. Za pomocą tego typu środowiska, możesz testować wprowadzane zmiany, bez wywierania wpływu na innych członków zespołu. Po zakończeniu wprowadzania zmian, możesz sprawdzić pliki do kontroli wersji, gdy inni członkowie zespołu mogą uzyskać zmiany i tworzyć i wdrażać je na serwer testowy.|-   [Zapytania i edytorów tekstu (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327)<br />-   [Debuger języka Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324)|
|**Tworzenie prototypów, sprawdzanie wyników testów i modyfikowania skryptów bazy danych i obiektów:** można użyć [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] edytora, aby wykonać dowolne spośród tych wspólnych zadań.|-   [Zapytania i edytorów tekstu (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327)|

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
