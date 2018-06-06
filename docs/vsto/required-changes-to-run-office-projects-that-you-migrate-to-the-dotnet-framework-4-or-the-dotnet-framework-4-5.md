---
title: Zmiany wymagane w celu uruchamiania projektów pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 53a6b138509648af102a50217a8bab4d32b27a2a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693919"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Zmiany wymagane w celu uruchamiania projektów pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5
  Jeśli platforma docelowa programu Office project jest zmieniana na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później ze starszej wersji programu .NET Framework, należy wykonać następujące zadania, aby upewnić się, że rozwiązanie może działać na komputerze dewelopera i na komputerach użytkowników końcowych:  
  
-   Usuń <xref:System.Security.SecurityTransparentAttribute> z projektu po uaktualnieniu z programu Visual Studio 2008.  
  
-   Wykonaj **wyczyść** polecenia w programie Visual Studio, aby można było uruchomić ani debugować projektu na komputerze dewelopera.  
  
-   Aktualizacja programu .NET Framework wymagań wstępnych dla projektu.  
  
-   Użytkownicy końcowi również należy ponownie zainstalować rozwiązania, jeśli wcześniej wdrożona przy użyciu technologii ClickOnce, przed zmianą platformy docelowej.  
  
 Aby uzyskać więcej informacji na temat każdego z tych zadań Zobacz odpowiedniej sekcji poniżej.  
  
## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Usuń atrybut SecurityTransparent projektach, które w przypadku uaktualniania z programu Visual Studio 2008  
 Po uaktualnieniu projektu pakietu Office w Visual Studio 2008 i platformę docelową projektu następnie zmienia się na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy usunąć <xref:System.Security.SecurityTransparentAttribute> z projektu. Program Visual Studio nie są automatycznie usuwane ten atrybut dla Ciebie. Jeśli ten atrybut nie zostanie usunięty, zostanie wyświetlony komunikat o błędzie podczas kompilowania projektu.  
  
 Aby uzyskać więcej informacji o warunkach, w których program Visual Studio można zmienić platformę docelową ulepszonych projektów do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], zobacz [uaktualnienia i migracja rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
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
  
## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Wykonaj czystą polecenie, aby debugować ani uruchamiać projektu na komputerze dewelopera  
 Jeśli projekt pakietu Office został utworzony przed platformy docelowej projektu została zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy wykonać **wyczyść** poleceń i ponownie skompilować projekt po zmianie platformy docelowej. Jeśli nie wykonuj **wyczyść** polecenia, zostanie wyświetlony <xref:System.Runtime.InteropServices.COMException> podczas próby debugować ani uruchamiać retargeted projektu.  
  
 Aby uzyskać więcej informacji na temat **wyczyść** polecenia, zobacz [rozwiązań Office kompilacji](../vsto/building-office-solutions.md).  
  
## <a name="update-the-prerequisites-for-deployment"></a>Wymagania wstępne dotyczące wdrażania aktualizacji  
 Gdy Przekieruj Office project, aby [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy również zaktualizować odpowiedni wstępnie wymaganego programu .NET Framework w **wymagania wstępne** okno dialogowe. W przeciwnym razie wdrażania ClickOnce lub projekt InstallShield Limited Edition wyszukuje i instaluje poprzedniej wersji programu .NET Framework.  
  
 Aby uzyskać więcej informacji o aktualizowaniu wymagania wstępne dotyczące wdrażania na komputerach użytkowników końcowych, zobacz [porady: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstall-solutions-on-end-user-computers"></a>Zainstaluj ponownie rozwiązań na komputerach użytkowników końcowych  
 Jeśli użycie technologii ClickOnce do wdrażania rozwiązania pakietu Office, przeznaczonego dla programu .NET Framework 3.5, a następnie przekierować projektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, użytkownicy końcowi muszą odinstalować rozwiązanie, a następnie zainstaluj ponownie rozwiązanie, po ją opublikować. Jeśli opublikować retargeted rozwiązania i rozwiązanie jest aktualizowana na komputerach użytkowników końcowych, użytkownicy końcowi będą otrzymywać <xref:System.Runtime.InteropServices.COMException> po uruchomieniu zaktualizowane rozwiązanie.  
  
## <a name="see-also"></a>Zobacz także  
 [Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  