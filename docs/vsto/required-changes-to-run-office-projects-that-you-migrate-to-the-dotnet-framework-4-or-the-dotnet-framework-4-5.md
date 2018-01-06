---
title: "Wymagane zmiany w celu uruchamiania projektów pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d395492d030728e65eb5e35b053641f0b684da2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Zmiany wymagane w celu uruchamiania projektów związanych z pakietem Office przenoszonych do oprogramowania .NET Framework w wersji 4 lub 4.5
  Jeśli platforma docelowa programu Office project jest zmieniana na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później ze starszej wersji programu .NET Framework, należy wykonać następujące zadania, aby upewnić się, że rozwiązanie może działać na komputerze dewelopera i na komputerach użytkowników końcowych:  
  
-   Usuń <xref:System.Security.SecurityTransparentAttribute> z projektu po uaktualnieniu z programu Visual Studio 2008.  
  
-   Wykonaj **wyczyść** polecenia w programie Visual Studio, aby można było uruchomić ani debugować projektu na komputerze dewelopera.  
  
-   Aktualizacja programu .NET Framework wymagań wstępnych dla projektu.  
  
-   Użytkownicy końcowi również należy ponownie zainstalować rozwiązania, jeśli wcześniej wdrożona przy użyciu technologii ClickOnce, przed zmianą platformy docelowej.  
  
 Aby uzyskać więcej informacji na temat każdego z tych zadań Zobacz odpowiedniej sekcji poniżej.  
  
## <a name="removing-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Usuwanie atrybutów SecurityTransparent projektach, które w przypadku uaktualniania z programu Visual Studio 2008  
 Po uaktualnieniu projektu pakietu Office w Visual Studio 2008 i platformę docelową projektu następnie zmienia się na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy usunąć <xref:System.Security.SecurityTransparentAttribute> z projektu. Program Visual Studio nie są automatycznie usuwane ten atrybut dla Ciebie. Jeśli ten atrybut nie zostanie usunięty, zostanie wyświetlony komunikat o błędzie podczas kompilowania projektu.  
  
 Aby uzyskać więcej informacji o warunkach, w których program Visual Studio można zmienić platformę docelową ulepszonych projektów do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], zobacz [uaktualnianie i migracja rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>Aby usunąć atrybut SecurityTransparentAttribute  
  
1.  Otwórz projekt w programie Visual Studio Otwórz **Eksploratora rozwiązań**.  
  
2.  W obszarze **właściwości** węzeł (C#) lub **mój projekt** węzeł (Visual Basic), kliknij dwukrotnie plik kodu AssemblyInfo, aby otworzyć go w edytorze kodu.  
  
    > [!NOTE]  
    >  W projektach Visual Basic, należy kliknąć opcję **Pokaż wszystkie pliki** przycisk **Eksploratora rozwiązań** do znajduje się w pliku kodu AssemblyInfo.  
  
3.  Zlokalizuj <xref:System.Security.SecurityTransparentAttribute> i usuń go z pliku lub go komentarz.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="performing-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Wykonanie polecenia Wyczyść, aby debugować ani uruchamiać projektu na komputerze dewelopera  
 Jeśli projekt pakietu Office został utworzony przed platformy docelowej projektu została zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy wykonać **wyczyść** poleceń i ponownie skompilować projekt po zmianie platformy docelowej. Jeśli nie wykonuj **wyczyść** polecenia, zostanie wyświetlony <xref:System.Runtime.InteropServices.COMException> podczas próby debugować ani uruchamiać retargeted projektu.  
  
 Aby uzyskać więcej informacji na temat **wyczyść** polecenia, zobacz [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
## <a name="updating-the-prerequisites-for-deployment"></a>Wymagania wstępne dotyczące wdrażania aktualizacji  
 Gdy Przekieruj Office project, aby [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy również zaktualizować odpowiedni wstępnie wymaganego programu .NET Framework w **wymagania wstępne** okno dialogowe. W przeciwnym razie wdrażania ClickOnce lub projekt InstallShield Limited Edition wyszukuje i instaluje poprzedniej wersji programu .NET Framework.  
  
 Aby uzyskać więcej informacji o aktualizowaniu wymagania wstępne dotyczące wdrażania na komputerach użytkowników końcowych, zobacz [porady: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstalling-solutions-on-end-user-computers"></a>Ponowna instalacja rozwiązań na komputerach użytkowników końcowych  
 Jeśli użycie technologii ClickOnce do wdrażania rozwiązania pakietu Office, przeznaczonego dla programu .NET Framework 3.5, a następnie przekierować projektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, użytkownicy końcowi muszą odinstalować rozwiązanie, a następnie zainstaluj ponownie rozwiązanie, po ją opublikować. Jeśli opublikować retargeted rozwiązania i rozwiązanie jest aktualizowana na komputerach użytkowników końcowych, użytkownicy końcowi będą otrzymywać <xref:System.Runtime.InteropServices.COMException> po uruchomieniu zaktualizowane rozwiązanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  