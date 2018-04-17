---
title: Baza danych projektów, projektów serwera i DAC projekty w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: baca17712d6cf39753dab51c60fee901c0ea08ca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Projektów baz danych i aplikacji warstwy danych w programie Visual Studio  
Projektów bazy danych służy do tworzenia nowych baz danych, nowych aplikacji warstwy danych (DAC) oraz do aktualizowania istniejących baz danych oraz aplikacji warstwy danych. Zarówno projektów bazy danych, jak i projektów DAC umożliwiają dotyczą metody zarządzania projektu i kontroli wersji wysiłków programowanie bazy danych w podobny sposób zastosowania tych metod do kodu zarządzanego i natywnego. Może ułatwić zarządzanie zmianami do baz danych i serwerów baz danych przez utworzenie zespołu deweloperów *projektu DAC*, *projekt bazy danych*, lub *Projekt serwera* i umieścić go w ramach kontroli wersji. Członkowie zespołu można zapoznać się z plików podejmowaniu, tworzenie i testowanie zmian w *izolowane środowisko*, lub piaskownicy przed udostępnieniem je zespołowi. Aby zapewnić jakości kodu, zespołu Zakończ i przetestować w środowisku przemieszczania wszystkich zmian dla konkretnej wersji bazy danych, przed wdrożeniem zmian w środowisku produkcyjnym.  
  
Aby uzyskać listę funkcji bazy danych, które są obsługiwane przez aplikacje warstwy danych, zobacz [funkcje obsługiwane w aplikacji warstwy danych](http://go.microsoft.com/fwlink/?LinkId=164239) w witrynie sieci web firmy Microsoft. Jeśli używasz funkcji, które nie są obsługiwane przez aplikacje warstwy danych w bazie danych, należy zamiast tego użyć projekt bazy danych do zarządzania zmianami w bazie danych.  
  
## <a name="common-high-level-tasks"></a>Typowe zadania wysokiego poziomu  
  
|Zadania wysokiego poziomu|Zawartość pomocnicza|  
|----------------------|------------------------|  
|**Rozpocząć programowanie aplikacji warstwy danych:** A DAC jest nowe pojęcie wprowadzone w systemie [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] zawierający definicję [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych i towarzyszące wystąpienia obiektów, które są używane przez serwer klienta lub 3-warstwowej aplikacja. DAC zawiera obiekty bazy danych, takie jak tabele i widoki, wraz z wystąpienia jednostki, takich jak nazwy logowania. Można użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do utworzenia projektu aplikacji DAC, tworzenia pliku pakietu aplikacji DAC i wysyłania tego pliku pakietu aplikacji DAC do administratora bazy danych w celu wdrożenia na wystąpienie [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] aparatu bazy danych.|-   [Tworzenie i zarządzanie nimi aplikacji warstwy danych](http://go.microsoft.com/fwlink/?LinkId=160741) (witrynę sieci web firmy Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Wykonywanie tworzenia interakcyjnych baz danych:** Jeśli jesteś deweloperem lub tester, zapoznaj się z części projektu, a następnie zaktualizuj je w środowisku projektowym izolowanym. Za pomocą takiego środowiska, można sprawdzić zmiany bez wpływu na innych członków zespołu. Po zakończeniu wprowadzania zmian, możesz sprawdzić pliki do kontroli wersji, gdzie innych członków zespołu można uzyskać zmiany i tworzenia i wdrażania ich na serwerze testowym.|-   [Zapytanie i edytory tekstów (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (witrynę sieci web firmy Microsoft)<br />-   [Debuger języka Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (witrynę sieci web firmy Microsoft)|  
|**Tworzenie prototypów, weryfikowanie przetestować wyniki oraz modyfikowanie skryptów bazy danych i obiektów:** można użyć [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] edytora w celu wykonania tych zadań.|-   [Zapytanie i edytory tekstów (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (witrynę sieci web firmy Microsoft)|  
  
## <a name="see-also"></a>Zobacz także
[Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
