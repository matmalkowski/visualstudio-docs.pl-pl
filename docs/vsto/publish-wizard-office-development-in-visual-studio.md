---
title: Publikowanie kreatora (Office Development w Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 43b4869435c34a29cac5fd18a13d2b4b140e8b6c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Kreator publikacji (Office Development w Visual Studio)
  Użyj **Kreator publikowania** Aby skopiować pliki rozwiązania do określonej lokalizacji, Utwórz plik manifestu, a następnie utwórz program instalacyjny.  
  
 Aby uzyskać dostęp do tego kreatora na **kompilacji** menu, wybierz **publikowania** *Nazwa rozwiązania*. Można także przejść do **Kreator publikowania** z **Eksploratora rozwiązań**. Otwórz menu skrótów węzła projektu, a następnie wybierz pozycję **publikowania**.  
  
 Poniższa sekcja zawiera opis strony kreatora.  
  
## <a name="where-do-you-want-to-publish-the-application"></a>Gdzie chcesz opublikować aplikację?  
 **Określ lokalizację do publikowania tej aplikacji**  
 Wymagany. Lokalizacji publikacji jest to katalog gdzie **Kreator publikowania** kopiuje pliki rozwiązania, takie jak manifesty, zestawy tymczasowe certyfikatu i innych plików z kompilacji. Musi mieć dostęp do zapisu do tego katalogu.  
  
 Wpisz lokalizację jako ścieżkę dysku, udziału plików, witryny FTP lub adres URL witryny sieci web, lub kliknij przycisk **Przeglądaj** przycisk, aby wyszukać lokalizację. Ścieżka może być w tych formatach:  
  
-   Ścieżka względna lub bezwzględna w standardowym formacie systemu Windows, takich jak C:\Deploy\MyApplication lub \MyApplication.  
  
-   Ścieżka Universal Naming Convention (UNC), takich jak \\\ServerName\MyApplication\\.  
  
-   Adres URL witryny sieci web, takich jak http://www.microsoft.com/MyApplication.  
  
 Domyślnie jest lokalizację publikowania *http://localhost/projectname/* usługi IIS są zainstalowane, czy katalog publish\, jeśli chcesz nie IIS zainstalowana.  
  
> [!NOTE]  
>  Istnieje więcej uwagi dotyczące komputera docelowego jest uruchomiony system Windows Vista. Musi być administratorem na komputerze z systemem Windows Vista do korzystania z opcji publikowania lokalnych. Ponadto domyślna lokalizacja to zawsze *publikowania\\*  katalogu, niezależnie od tego, czy zostały zainstalowane usługi IIS.  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Co to jest domyślna ścieżka instalacji na komputerach użytkowników końcowych?  
 Ścieżka instalacji jest opcjonalne. Można ustawić ścieżkę instalacji później, jeśli wolisz. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie ścieżki instalacji rozwiązania do pakietu Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 Ścieżka instalacji jest katalogu, z którego użytkownik końcowy zainstaluje dostosowań. Istnieje również ścieżki, który rozwiązanie będzie używany do sprawdzania aktualizacji. **Kreator publikowania** nie wdrażania rozwiązania do tej lokalizacji, chyba że ścieżka jest taka sama jak wprowadzona w **Określ lokalizację do publikowania tej aplikacji** pole na poprzedniej stronie.  
  
 **Z witryny sieci Web**  
 Podaj adres URL, które użytkownicy końcowi będą wykonać, aby zainstalować rozwiązania.  
  
 **Z udziału UNC ścieżki lub pliku**  
 Określ ścieżkę UNC, które użytkownicy końcowi będą wykonać, aby zainstalować rozwiązania.  
  
 **Z dysku CD-ROM lub DVD-ROM**  
 Ta opcja nie wymaga ścieżkę instalacji.  
  
 Program Visual Studio nie nagrywanie, CD lub DVD. Należy skopiować ręcznie dane wyjściowe z dysku CD lub DVD.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Publikowanie strony, Projektant projektu &#40; programowanie Office w Visual Studio &#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
  