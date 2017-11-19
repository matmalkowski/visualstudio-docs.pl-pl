---
title: "Kod zabezpieczeń dostępu dla aplikacji ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
caps.latest.revision: "31"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: ac2da96844587401a7156669e79a9bdcfe750070
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="code-access-security-for-clickonce-applications"></a>Zabezpieczenia dostępu kodu dla aplikacji ClickOnce
ClickOnce — aplikacje są oparte na programie .NET Framework i obowiązują ograniczenia zabezpieczeń dostępu kodu. Dlatego jest ważne, że rozumiesz konsekwencje kod dostępu zabezpieczeń i w związku z tym zapisu aplikacji ClickOnce.  
  
 Zabezpieczenia dostępu kodu jest mechanizm w programie .NET Framework, która pomaga ograniczyć dostępu kodu do chronionych zasobów i operacji. Należy skonfigurować uprawnienia zabezpieczeń dostępu kodu dla aplikacji ClickOnce używać strefy lokalizacji Instalatora aplikacji. W większości przypadków można **Internet** strefę dla ograniczony zestaw uprawnień lub **lokalny Intranet** strefę dla większy zestaw uprawnień.  
  
## <a name="default-clickonce-code-access-security"></a>Zabezpieczenia dostępu kodu ClickOnce domyślne  
 Domyślnie aplikacji ClickOnce otrzymuje uprawnienia pełnego zaufania, jeśli jest zainstalowana lub uruchomić na komputerze klienckim.  
  
-   Aplikacja mająca uprawnienia pełnego zaufania ma nieograniczony dostęp do zasobów, takich jak system plików i rejestru. Umożliwia potencjalnie aplikacji (i systemu przez użytkownika końcowego) została wykorzystana przez złośliwy kod.  
  
-   Jeśli aplikacja wymaga uprawnień pełnego zaufania, użytkownik końcowy może monit o uprawnienia do aplikacji. To oznacza, że aplikacja nie zapewnia naprawdę środowisko ClickOnce, a monit potencjalnie może być trudne dla mniej doświadczeni użytkownicy.  
  
    > [!NOTE]
    >  Podczas instalowania aplikacji z nośników wymiennych, takich jak dysku CD, użytkownik nie jest monitowany. Ponadto administrator sieci można skonfigurować zasady sieci, dzięki czemu użytkownicy nie są monitowani o podczas instalacji aplikacji z zaufanego źródła. Aby uzyskać więcej informacji, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
 Aby ograniczyć uprawnienia dla aplikacji ClickOnce, można zmodyfikować uprawnienia zabezpieczeń dostępu kodu dla aplikacji do strefy, która najlepiej odpowiada uprawnienia wymagane przez aplikację żądań. W większości przypadków można wybrać strefy, z której aplikacja jest wdrażana. Na przykład jeśli aplikacja jest aplikacja przedsiębiorstwa, można użyć **lokalny Intranet** strefy. Jeśli aplikacja jest aplikacji internetowej, możesz użyć **Internet** strefy.  
  
## <a name="configuring-security-permissions"></a>Konfigurowanie uprawnień zabezpieczeń  
 Zawsze należy skonfigurować musi spełniać aplikacja ClickOnce do żądania odpowiedniej strefy, aby ograniczyć uprawnienia zabezpieczeń dostępu kodu. Można skonfigurować uprawnienia zabezpieczeń na **zabezpieczeń** strony **projektanta projektu**.  
  
 **Zabezpieczeń** strony **projektanta projektu** zawiera **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru. Gdy to pole wyboru jest zaznaczone, żądania uprawnień zabezpieczeń są dodawane do manifest wdrażania aplikacji. Podczas instalacji użytkownik wyświetli monit o uprawnienia domyślne uprawnienia dla tej strefy, z której aplikacja jest wdrażana przekroczona żądanych uprawnień. Aby uzyskać więcej informacji, zobacz [porady: włączanie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 Aplikacje wdrożone z różnych lokalizacji są przyznawane różnych poziomów uprawnień bez monitowania. Na przykład gdy aplikacja jest wdrażana z Internetu, otrzymuje wysokiej restrykcyjny zestaw uprawnień. Podczas instalowania z lokalny Intranet, odbierze więcej uprawnień, a podczas instalowania z dysku CD, otrzyma uprawnienia pełnego zaufania.  
  
 Jako punktu wyjścia do konfigurowania uprawnień, można wybrać strefy zabezpieczeń z **strefy** listy na **zabezpieczeń** strony. Jeśli aplikacja zostanie wdrożona potencjalnie z więcej niż jednej strefie, wybierz strefę o najniższych uprawnień. Aby uzyskać więcej informacji, zobacz [porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 Właściwości, które można ustawić zależy od zestawu uprawnień; nie wszystkie zestawy uprawnień mają można skonfigurować właściwości. Aby uzyskać więcej informacji o pełną listę uprawnień, które mogą żądać aplikacji, zobacz <xref:System.Security.Permissions>. Aby uzyskać więcej informacji na temat ustawiania uprawnień niestandardowych strefy, zobacz [porady: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## <a name="debugging-an-application-that-has-restricted-permissions"></a>Debugowanie aplikacji, która ma ograniczone uprawnienia  
 Deweloperzy najprawdopodobniej uruchom komputer deweloperski z uprawnieniami pełnego zaufania. W związku z tym nie ma tego samego wyjątki zabezpieczeń podczas debugowania aplikacji, które użytkownicy mogą zobaczyć, jeśli są uruchamiane z ograniczonymi uprawnieniami.  
  
 Aby przechwytywać tych wyjątków, musisz debugowania aplikacji z takimi samymi uprawnieniami jak użytkownika końcowego. Debugowanie z ograniczonymi uprawnieniami można włączyć dla **zabezpieczeń** strony **projektanta projektu**.  
  
 Podczas debugowania aplikacji z ograniczonymi uprawnieniami wyjątki zostanie wygenerowany dla dowolnego żądania kontroli zabezpieczeń kodu, które nie zostały włączone na **zabezpieczeń** strony. Zostanie wyświetlony pomocnika wyjątków, zapewniając sugestie dotyczące sposobu modyfikowania kodu, aby zapobiec wyjątek.  
  
 Ponadto podczas pisania kodu, funkcję IntelliSense w edytorze kodu spowoduje wyłączenie żadnych elementów członkowskich, które nie znajdują się w obszarze uprawnienia zabezpieczeń, które zostały skonfigurowane.  
  
 Aby uzyskać więcej informacji, zobacz [porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>Uprawnienia zabezpieczeń aplikacje obsługiwane w przeglądarce  
 Program Visual Studio oferuje następujące typy projektu dla aplikacji Windows Presentation Foundation (WPF):  
  
-   WPF aplikacji systemu Windows  
  
-   Aplikacja przeglądarki sieci Web WPF  
  
-   Biblioteka kontrolek niestandardowych WPF  
  
-   Biblioteka usługi WPF  
  
 Z tych typów projektów tylko WPF aplikacji przeglądarki sieci Web są obsługiwane w przeglądarce sieci Web i dlatego wymaga specjalnych wdrożenia i ustawienia zabezpieczeń. Domyślne ustawienia zabezpieczeń dla tych aplikacji, są następujące:  
  
-   **Włączanie ustawień zabezpieczeń technologii ClickOnce**  
  
-   **To jest częściowo zaufanych aplikacji**  
  
-   **Strefy internetowej** (z domyślnego zestawu uprawnień dla aplikacji przeglądarki sieci Web WPF wybrane)  
  
 W **Zaawansowane ustawienia zabezpieczeń** okno dialogowe **Debuguj aplikację z wybranym zestawem uprawnień** pole wyboru jest zaznaczone i wyłączone. Jest to spowodowane debugowania w strefie nie może zostać wyłączone dla aplikacji hostowanej w przeglądarce.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Porady: włączanie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Strona zabezpieczeń, Projektant projektu](../ide/reference/security-page-project-designer.md)