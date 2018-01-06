---
title: "Zaufane Omówienie wdrożenia aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: "31"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 34e83d6b035ba6ea91190fa89b9e1a63366e7907
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="trusted-application-deployment-overview"></a>Przegląd wdrażania zaufanych aplikacji
Ten temat zawiera omówienie sposobu wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, które mają podwyższony poziom uprawnień za pomocą technologii zaufane wdrożenia aplikacji.  
  
 Zaufane wdrożenia aplikacji, część [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologii wdrażania ułatwia organizacjom o dowolnym rozmiarze udzielać dodatkowych uprawnień do zarządzanych aplikacji w sposób bezpieczniejsze i bezpieczniejsze bez monitowania użytkownika. Z zaufanych wdrożenia aplikacji organizacja może skonfigurować tylko na kliencie, aby wyświetlić listę zaufanych wydawców, którzy są identyfikowane za pomocą certyfikatów Authenticode. Następnie dowolne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji podpisanej przez jeden z tych zaufanych wydawców otrzymuje wyższy poziom zaufania.  
  
> [!NOTE]
>  Zaufane wdrożenie aplikacji wymaga jednorazowej konfiguracji komputera użytkownika. W zarządzanym środowisku pulpitu tę konfigurację można przeprowadzić za pomocą zasad globalnych. Jeśli to nie chcesz dla aplikacji, należy użyć podniesienia uprawnień. Aby uzyskać więcej informacji, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="trusted-application-deployment-basics"></a>Podstawy wdrażania zaufanych aplikacji  
 W poniższej tabeli przedstawiono te obiekty i role, które są związane z we wdrożeniu aplikacji zaufanej.  
  
|Obiekt lub roli|Opis|  
|--------------------|-----------------|  
|Administrator|Jednostka organizacyjna, która jest odpowiedzialna za aktualizacji i obsługę komputerów klienckich|  
|Menedżera zaufania|Podsystem w środowisko uruchomieniowe języka wspólnego (CLR) obowiązek stosować zabezpieczeń aplikacji klienta.|  
|Wydawcy|Jednostka, która zapisuje i obsługiwanej aplikacji.|  
|Narzędzie wdrażania|Jednostka, która pakietów i rozpowszechnia aplikacji dla użytkowników.|  
|certificate|Podpis kryptograficznego, który zawiera klucz publiczny i prywatny; Ogólnie rzecz biorąc wystawiony przez urząd certyfikacji (CA) można ciesząca dla jego autentyczności.|  
|Certyfikatu Authenticode|Certyfikat z osadzone metadane opisujące, między innymi zastosowań, dla których można zastosować certyfikat.|  
|Urząd certyfikacji|Organizacja, która weryfikuje tożsamość wydawcy i wystawia, ich certyfikaty osadzonych metadanych wydawcy.|  
|główny urząd certyfikacji|Urząd certyfikacji, który zezwala na inne urzędy certyfikacji do wystawiania certyfikatów.|  
|Kontener kluczy|Logicznego miejsca do magazynowania w systemie Microsoft Windows przechowywania certyfikatów.|  
|zaufanego wydawcy|Wydawca, którego certyfikat Authenticode został dodany do listy zaufania certyfikatów (CTL) na komputerze klienckim.|  
  
 W większych organizacji wydawcy i wdrażania są często dwa osobne jednostki:  
  
-   Wydawca jest grupa, która tworzy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
-   Narzędzia wdrażania jest grupa, zazwyczaj dział technologii informatycznych (IT) informacje, który rozprowadza [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji na komputerach stacjonarnych korporacyjnym środowisku.  
  
 Należy wykonać następujące kroki, aby móc korzystać z zaufanego wdrożenia aplikacji:  
  
1.  Uzyskaj certyfikat dla wydawcy.  
  
2.  Dodaj wydawcy do magazynu zaufanych wydawców na wszystkich klientach.  
  
3.  Tworzenie sieci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
4.  Zaloguj się manifest wdrażania z certyfikatem wydawcy.  
  
5.  Opublikuj wdrożenia aplikacji na komputerach klienckich.  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>Uzyskaj certyfikat dla wydawcy  
 Certyfikaty cyfrowe są podstawowym składnikiem systemu zabezpieczeń i uwierzytelniania Microsoft Authenticode. Authenticode jest standardowym elementem systemu operacyjnego Windows. Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje muszą być podpisane za pomocą certyfikatu cyfrowego, niezależnie od tego, czy udział we wdrożeniu aplikacji zaufanych. Pełne wyjaśnienie działania Authenticode z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], zobacz [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Dodać wydawcę w magazynie zaufanych wydawców  
 Dla Twojego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji na odbieranie wyższy poziom zaufania, musisz dodać certyfikat jako zaufanego wydawcy do każdego komputera klienckiego, na którym będzie uruchomiona aplikacja. Wykonanie tego zadania jest jednorazowej konfiguracji. Po jego ukończeniu można wdrożyć jako wiele [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje podpisane z certyfikatem wydawcy ma, a wszystkie uruchomieniem z wysokim poziomem zaufania.  
  
 Jeśli wdrażasz aplikację w środowisku zarządzanym pulpitu; na przykład firmowego intranetu z systemu operacyjnego Windows; Tworząc nową listę zaufania certyfikatów (CTL) przy użyciu zasad grupy może dodawać zaufanych wydawców do magazynu klienta. Aby uzyskać więcej informacji, zobacz [utworzyć listę zaufania certyfikatów dla obiekt zasad grupy](http://go.microsoft.com/fwlink/?LinkId=102576).  
  
 Jeśli nie wymaga wdrażania aplikacji w środowisku zarządzanym pulpitu, dostępne są następujące opcje Dodawanie certyfikatu do magazynu zaufanego wydawcy:  
  
-   <xref:System.Security.Cryptography?displayProperty=fullName> Przestrzeni nazw.  
  
-   CertMgr.exe, który jest składnikiem programu Internet Explorer i w związku z tym istnieje w systemach Windows 98 i wszystkich nowszych wersji. Aby uzyskać więcej informacji, zobacz [Certmgr.exe (Menedżer certyfikatów narzędzie)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).  
  
### <a name="create-a-clickonce-application"></a>Tworzenie aplikacji ClickOnce  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] aplikacji klienckiej połączone z manifestu plików, które opisują aplikacji i podać parametry instalacji. Można włączyć program do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji za pomocą **publikowania** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Alternatywnie można wygenerować wszystkie pliki wymagane do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia przy użyciu narzędzia, które są dołączone do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Aby uzyskać szczegółowe instrukcje dotyczące [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrażania, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 Wdrażanie zaufanej aplikacji jest specyficzna dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]i można używać tylko z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
### <a name="sign-the-deployment"></a>Zaloguj się wdrożenia  
 Po uzyskaniu certyfikatu, należy użyć go do podpisania wdrożenia. Jeśli wdrażana aplikacja za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kreator publikowania, Kreator automatycznie wygeneruje certyfikat testowy dla Ciebie, jeśli nie określono certyfikatu użytkownika. Można również użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okna Projektanta projektu, aby przekazać certyfikat dostarczony przez urząd certyfikacji.  Zobacz też [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji] (http://msdn.microsoft.com/library/31kztyey\(v=vs.110\).  
  
> [!CAUTION]
>  Nie zaleca się że aplikację można wdrożyć przy użyciu certyfikatu testowego.  
  
 Możesz również utworzyć aplikację przy użyciu narzędzia Mage.exe lub MageUI.exe zestawu SDK. Aby uzyskać więcej informacji, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Aby uzyskać pełną listę opcji wiersza polecenia dotyczące podpisywania wdrożenia, zobacz [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
### <a name="publish-the-application"></a>Publikowanie aplikacji  
 Zaraz po zarejestrowaniu Twojego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestów, aplikacja jest gotowa do publikowania w lokalizacji instalacji. W wybranej lokalizacji instalacji można serwera sieci Web, udział plików lub dysk lokalny. Gdy klient uzyskuje dostęp do manifest wdrażania po raz pierwszy, musisz wybrać menedżera zaufania czy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji udzielono uprawnienia lub aby nie było uruchamiane na wyższym poziomie zaufania zainstalowana nieoczekiwanych wydawcy. Menedżera zaufania sprawia, że ten wybór porównując certyfikat użyty do podpisania wdrożenia za pomocą certyfikatów przechowywanych w klienta zaufanego wydawcy przechowywania. Jeśli Menedżera zaufania znalezienia dopasowania, aplikacja zostanie uruchomiona z wysokim poziomem zaufania.  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>Wdrażanie zaufanej aplikacji i podniesienie uprawnień  
 Bieżący wydawca nie jest zaufanym wydawcą, Menedżera zaufania użyje podniesienia uprawnień do badania użytkownika o Określa, czy użytkownik chce udzielić aplikacji podniesionych uprawnień. Jeśli podniesienie uprawnień jest wyłączona przez administratora, jednak aplikacja nie może uzyskać uprawnienia do uruchamiania. Aplikacja nie będzie działać i prezentowane żadne powiadomienie będzie widoczny dla użytkownika. Aby uzyskać więcej informacji na temat podniesienia uprawnień, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="limitations-of-trusted-application-deployment"></a>Ograniczenia wdrażanie zaufanej aplikacji  
 Wdrażanie zaufanej aplikacji można użyć udzielenia zaufania z podwyższonym poziomem uprawnień, aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje wdrożone za pośrednictwem sieci Web lub za pośrednictwem udziału plików w organizacji. Nie masz przy użyciu zaufanego wdrażania aplikacji dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji rozproszonych dysku CD, ponieważ domyślnie te aplikacje są udzielane pełne zaufanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
