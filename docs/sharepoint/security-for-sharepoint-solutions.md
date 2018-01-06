---
title: "Zabezpieczenia dla rozwiązań SharePoint | Dokumentacja firmy Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 22ef16c40fb2d70ae7e1b835860b74843abe57d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-for-sharepoint-solutions"></a>Zabezpieczenia dla rozwiązań SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]zawiera następujące funkcje w celu poprawy zabezpieczeń aplikacji programu SharePoint.  
  
## <a name="safe-control-entries"></a>Wpisy kontroli bezpieczne  
 Każdy element projektu SharePoint utworzone w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ma **bezpieczne wpisy kontroli** właściwość, która reprezentuje sejfie formanty kolekcji. Jego **bezpieczne** podwłaściwości umożliwia określenie formantów, które należy wziąć pod uwagę bezpieczne. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) i [określenie bezpiecznych składników Web Part](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## <a name="allowpartiallytrustedcallers-attribute"></a>Atrybut AllowPartiallyTrustedCallers  
 Domyślnie tylko aplikacje, które są w pełni zaufana przez system zabezpieczeń (CAS) środowiska uruchomieniowego kodów dostępu mają dostęp do zestaw udostępnionego kodu zarządzanego. Oznaczenie zestawem całkowicie zaufanym o atrybucie AllowPartiallyTrustedCallers zezwala na częściowo zaufane zestawy do niego dostęp.  
  
 Wszystkie rozwiązania programu SharePoint, która nie została wdrożona z pamięci podręcznej GAC jest dodawany atrybut AllowPartiallyTrustedCallers ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). W tym rozwiązania w trybie piaskownicy lub rozwiązania wdrożone do katalogu Bin aplikacji programu SharePoint. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń wersji 1 dla programu Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) i [wdrażanie części sieci Web w programie SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## <a name="safe-against-script-property"></a>Bezpieczne dla właściwości skryptu  
 *Skrypt iniekcji* jest wstawienie potencjalnie złośliwego kodu do formantów lub strony sieci Web. Aby lepiej chronić witryny programu SharePoint 2010, przed uruchomienie skryptu, współautorzy nie można wyświetlić ani edytować części sieci Web lub ich właściwości domyślnie. To zachowanie jest kontrolowana przez SafeControl — atrybut o nazwie SafeAgainstScript. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], atrybut ten element projektu **bezpieczne wpisy kontroli** podwłaściwości **bezpieczne skryptu przed**. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) i [porady: Oznacz kontrolek pojęciem bezpiecznych kontrolek](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## <a name="vista-and-windows-7-user-account-control"></a>Kontrola konta użytkownika 7 Vista i Windows  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]i [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] dołączyć do nich to funkcja zabezpieczeń, znane jako kontroli konta użytkownika (UAC). Umożliwiające tworzenie rozwiązań programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] i [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] systemów kontroli konta użytkownika, użytkownik musi uruchomić [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] administrator systemu. Z **Start** menu, otwórz menu skrótów [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], a następnie wybierz pozycję **Uruchom jako administrator**.  
  
 Aby skonfigurować [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] skrót do zawsze Uruchom jako administrator, otwórz menu skrótów, wybierz pozycję **właściwości**, wybierz **zaawansowane** przycisk **właściwości**— okno dialogowe, a następnie wybierz **Uruchom jako administrator** pole wyboru.  
  
 Aby uzyskać więcej informacji, zobacz [opis i konfigurowanie Kontrola konta użytkownika w systemie Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). i [Kontrola konta użytkownika systemu Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## <a name="sharepoint-permissions-considerations"></a>Uwagi dotyczące uprawnień programu SharePoint  
 Umożliwiające tworzenie rozwiązań programu SharePoint, musi mieć wystarczające uprawnienia do uruchamiania i debugowanie rozwiązań SharePoint. Zanim można przetestować rozwiązania programu SharePoint, wykonaj następujące kroki, aby upewnić się, że masz wystarczające uprawnienia:  
  
1.  Dodaj konto użytkownika jako administratora w systemie.  
  
2.  Dodaj konto użytkownika jako administratora farmy programu SharePoint server.  
  
    1.  Administracja centralna programu SharePoint 2010, wybierz **zarządzania do grupy administratorów farmy** łącza.  
  
    2.  Na **administratorzy farmy** wybierz pozycję **nowy** opcji menu  
  
3.  Dodaj konto użytkownika w grupie WSS_ADMIN_WPG uprawnienia.  
  
## <a name="additional-security-resources"></a>Zasoby dodatkowe zabezpieczenia  
 Aby uzyskać więcej informacji na temat problemów z zabezpieczeniami zobacz następujące tematy.  
  
### <a name="visual-studio-security"></a>Zabezpieczenia programu Visual Studio  
  
-   [Zabezpieczenia i uprawnienia użytkownika](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Zabezpieczenia w macierzystym i kodu platformy .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Zabezpieczenia w programie .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### <a name="sharepoint-security"></a>Zabezpieczenia programu SharePoint  
  
-   [Administracja programu SharePoint Foundation i zabezpieczenia](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Security Resource Center w programie SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Zabezpieczanie składników Web Part programu SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Poprawy zabezpieczeń aplikacji sieci Web: Zagrożenia i przeciwdziałanie](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### <a name="general-security"></a>Ogólne zabezpieczeń  
  
-   [Cykl życia tworzenia zabezpieczeń MSDN](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Tworzenie aplikacji ASP.NET bezpiecznego: Uwierzytelniania, autoryzacji i zapewnienia bezpiecznej komunikacji](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  