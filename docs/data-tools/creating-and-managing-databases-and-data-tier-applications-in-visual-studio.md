---
title: Projektów bazy danych, serwer projektów i DAC projekty w programie Visual Studio
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
ms.openlocfilehash: 03dca206f38d98c44e711e945f5d4015142f0af9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758410"
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Projektów baz danych i aplikacji warstwy danych w programie Visual Studio
Projektów bazy danych służy do tworzenia nowych baz danych, nowych aplikacji warstwy danych (DAC) oraz do aktualizowania istniejących baz danych oraz aplikacji warstwy danych. Zarówno projektów bazy danych, jak i projektów DAC umożliwiają dotyczą metody zarządzania projektu i kontroli wersji wysiłków programowanie bazy danych w podobny sposób zastosowania tych metod do kodu zarządzanego i natywnego. Możesz pomóc zespół deweloperów zarządzania zmianami do baz danych i serwerów baz danych, tworząc projekt aplikacji DAC, projekt bazy danych lub Projekt serwera i umieścić go w ramach kontroli wersji. Członkowie zespołu można następnie wyewidencjonować pliki, aby upewnij, tworzenie i testowanie zmian w środowisko projektowe izolowanej lub piaskownicy, przed udostępnieniem im z zespołem. Aby zapewnić jakości kodu, zespołu Zakończ i przetestować w środowisku przemieszczania wszystkich zmian dla konkretnej wersji bazy danych, przed wdrożeniem zmian w środowisku produkcyjnym.

Aby uzyskać listę funkcji bazy danych, które są obsługiwane przez aplikacje warstwy danych, zobacz [funkcje obsługiwane w aplikacji warstwy danych](http://go.microsoft.com/fwlink/?LinkId=164239) w witrynie sieci web firmy Microsoft. Jeśli używasz funkcji, które nie są obsługiwane przez aplikacje warstwy danych w bazie danych, należy zamiast tego użyć projekt bazy danych do zarządzania zmianami w bazie danych.

## <a name="common-high-level-tasks"></a>Typowe zadania wysokiego poziomu

|Zadania wysokiego poziomu|Zawartość pomocnicza|
|----------------------|------------------------|
|**Rozpocząć programowanie aplikacji warstwy danych:** A DAC jest nowe pojęcie wprowadzone w systemie [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] zawierający definicję [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych i towarzyszące wystąpienia obiektów, które są używane przez serwer klienta lub 3-warstwowej aplikacja. DAC zawiera obiekty bazy danych, takie jak tabele i widoki, wraz z wystąpienia jednostki, takich jak nazwy logowania. Służy do tworzenia projektu DAC, tworzenie pliku pakietu aplikacji DAC i wysłać ten plik pakietu aplikacji DAC do administratora bazy danych w celu wdrożenia na wystąpienie programu Visual Studio [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] aparatu bazy danych.|-   [Tworzenie i zarządzanie nimi aplikacji warstwy danych](http://go.microsoft.com/fwlink/?LinkId=160741) (witrynę sieci web firmy Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Wykonywanie tworzenia interakcyjnych baz danych:** Jeśli jesteś deweloperem lub tester, zapoznaj się z części projektu, a następnie zaktualizuj je w środowisku projektowym izolowanym. Za pomocą takiego środowiska, można sprawdzić zmiany bez wpływu na innych członków zespołu. Po zakończeniu wprowadzania zmian, możesz sprawdzić pliki do kontroli wersji, gdzie innych członków zespołu można uzyskać zmiany i tworzenia i wdrażania ich na serwerze testowym.|-   [Zapytanie i edytory tekstów (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (witrynę sieci web firmy Microsoft)<br />-   [Debuger języka Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (witrynę sieci web firmy Microsoft)|
|**Tworzenie prototypów, weryfikowanie przetestować wyniki oraz modyfikowanie skryptów bazy danych i obiektów:** można użyć [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] edytora w celu wykonania tych zadań.|-   [Zapytanie i edytory tekstów (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (witrynę sieci web firmy Microsoft)|

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
