---
title: Zabezpieczanie aplikacji ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/17/2017
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 8f41fb12c8ec9a5a3cec0a802f7fc5b4216a39d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="securing-clickonce-applications"></a>Zabezpieczanie aplikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje obowiązują ograniczenia zabezpieczeń dostępu kodu w programie .NET Framework, aby ograniczyć dostęp przez kod ma do chronionych zasobów i operacji. Z tego powodu, ważne jest, że rozumiesz konsekwencje zabezpieczenia dostępu kodu, aby zapisać Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji odpowiednio. W celu ograniczenia dostępu aplikacje mogą używać pełnego zaufania lub stref częściowych, takich jak strefy Internet i Intranet.  
  
 Ponadto technologia ClickOnce używa certyfikatów w celu weryfikowania autentyczności wydawcy aplikacji oraz podpisywania aplikacji i manifestów wdrożenia, co ma na celu zagwarantowanie, że pliki nie zostały w nieuprawniony sposób zmodyfikowane. Podpisywanie to opcjonalny krok, który ułatwia zmienianie plików aplikacji po wygenerowaniu manifestów. Jednak bez podpisanych manifestów trudno jest zagwarantować, że instalator aplikacji nie zostanie zmodyfikowany w wyniku ataku przeprowadzonego przez osobę z wewnątrz organizacji. Z tego powodu zaleca się podpisywanie aplikacji i manifestów wdrożenia, ponieważ pomaga to w zabezpieczaniu aplikacji.  
  
## <a name="zones"></a>Strefy  
 Aplikacje, które są wdrażane za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologii są ograniczone do zestawu uprawnień i akcje, które są zdefiniowane przez strefy zabezpieczeń. Strefy zabezpieczeń są zdefiniowane w programie Internet Explorer i są oparte na lokalizacji aplikacji. W poniższej tabeli wymieniono uprawnienia domyślne określone na podstawie lokalizacji wdrożenia:  
  
|Lokalizacja wdrożenia|Strefa zabezpieczeń|  
|-------------------------|-------------------|  
|Uruchamianie z sieci Web|Strefa Internet|  
|Instalacja z sieci Web|Strefa Internet|  
|Instalacja z sieciowego udziału plików|Strefa Lokalny intranet|  
|Instalacja z dysku CD-ROM|Pełne zaufanie|  
  
 Uprawnienia domyślne są określane na podstawie lokalizacji, z której została wdrożona oryginalna wersja aplikacji; aktualizacje aplikacji będą dziedziczyć te uprawnienia. Jeśli aplikacja jest skonfigurowana do sprawdzania, czy w sieci Web lub lokalizacji sieciowej są dostępne aktualizacje, oryginalna instalacja może otrzymać uprawienia dla strefy Internet lub Intranet, a nie uprawnienia pełnego zaufania. Aby zapobiec monitowaniu użytkowników, administrator systemu może określić zasady wdrażania technologii ClickOnce definiujące określonego wydawcę aplikacji jako zaufane źródło. Na komputerach, na których zostaną wdrożone te zasady, uprawnienia będą udzielane automatycznie i użytkownicy nie będą monitowani. Aby uzyskać więcej informacji, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md). Aby skonfigurować zaufane wdrożenie aplikacji, certyfikat można zainstalować na poziomie komputera lub przedsiębiorstwa. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Zasady zabezpieczeń dostępu kodu  
 Uprawnienia aplikacji są określane przez ustawienia [ \<trustinfo — > Element](../deployment/trustinfo-element-clickonce-application.md) elementu manifest aplikacji. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie generuje tych informacji zgodnie z ustawieniami projektu **zabezpieczeń** strony właściwości. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji otrzymuje tylko określone uprawnienia, które żądania. Na przykład w sytuacji, gdy dostęp do plików wymaga uprawnień pełnego zaufania, a aplikacja żąda uprawnienia dostępu do pliku, zostanie jej udzielone tylko uprawnienie dostępu do plików, a nie uprawnienia pełnego zaufania. Podczas tworzenia Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, należy upewnić się, że żądania tylko określone uprawnienia, które są wymagane przez aplikację. W większości przypadków można użyć stref Internet lub Lokalny intranet, aby ograniczyć aplikację do częściowego zaufania. Aby uzyskać więcej informacji, zobacz [porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Jeśli aplikacja wymaga uprawnień niestandardowych, można utworzyć strefę niestandardową. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Dołączenie uprawnienia, które nie wchodzi w skład domyślnego zestawu uprawnień dla strefy, z której została wdrożona aplikacja, spowoduje, że użytkownik końcowy będzie w czasie instalacji lub aktualizacji monitowany o udzielenie uprawnienia. Aby zapobiec monitowaniu użytkowników, administrator systemu może określić zasady wdrażania technologii ClickOnce definiujące określonego wydawcę aplikacji jako zaufane źródło. Na komputerach, na których zostaną wdrożone te zasady, uprawnienia będą udzielane automatycznie i użytkownicy nie będą monitowani.  
  
 Deweloper jest odpowiedzialny za zagwarantowanie, że jego aplikacja będzie działać z odpowiednimi uprawnieniami. Jeśli aplikacja w czasie wykonywania zażąda uprawnień spoza strefy, może wystąpić wyjątek zabezpieczeń. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umożliwia debugowanie aplikacji w strefie zabezpieczeń docelowej. i zawiera informacje pomocne w tworzeniu bezpiecznych aplikacji. Aby uzyskać więcej informacji, zobacz [porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Aby uzyskać więcej informacji o zabezpieczeniach dostępu kodu i ClickOnce, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certyfikaty podpisywania kodu  
 Aby opublikować aplikację przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrażania, można podpisać manifestów aplikacji i wdrażania aplikacji przy użyciu pary kluczy publiczny/prywatny. Narzędzia do podpisywania manifestu są dostępne w **podpisywanie** strony **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [strona podpisywania, Projektant projektu](../ide/reference/signing-page-project-designer.md). Alternatywnie można podpisać manifestów z plikiem klucza w procesie publikowania za pomocą Kreatora publikacji.  
  
 Po podpisaniu manifestów informacje o wydawcy określone na podstawie podpisu Authenticode będą wyświetlane użytkownikowi w oknie dialogowym uprawnień podczas instalacji, aby pokazać mu, że aplikacja pochodzi z zaufanego źródła.  
  
 Aby uzyskać więcej informacji na temat ClickOnce i certyfikatów, zobacz [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Uwierzytelnianie oparte na formularzach ASP.NET  
 Jeśli chcesz kontrolować wdrożeń, które każdy użytkownik może uzyskać dostęp, należy włączyć anonimowy dostęp do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje wdrożone na serwerze sieci Web. Zamiast tego należy umożliwić użytkownikom dostęp do zainstalowanych wdrożeń na podstawie tożsamości użytkownika, używając uwierzytelniania systemu Windows.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie obsługuje uwierzytelnianie oparte na formularzach ASP.NET, ponieważ używa ona trwałe pliki cookie; te stanowią zagrożenie dla bezpieczeństwa, ponieważ znajdują się w pamięci podręcznej programu Internet Explorer i może być zaatakowane. W związku z tym jeśli wdrażasz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, żadnym scenariuszu uwierzytelniania, oprócz uwierzytelniania systemu Windows nie jest obsługiwany.  
  
## <a name="passing-arguments"></a>Przekazywanie argumentów  
 Kwestią dodatkowe zabezpieczenia występuje, gdy trzeba przekazać argumenty do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Umożliwia deweloperom podać ciąg zapytania, aby aplikacje wdrożone za pośrednictwem sieci Web. Ciąg zapytania ma formę serii par nazwa-wartość umieszczonych na końcu adresu URL używanego do uruchamiania aplikacji:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Domyślnie argumenty ciągu zapytania są wyłączone. Aby je włączyć, atrybut `trustUrlParameters` musi być ustawiona w manifeście wdrażania aplikacji. Tę wartość można ustawić z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i z MageUI.exe. Aby uzyskać szczegółowe instrukcje dotyczące włączania przekazywanie ciągów zapytania, zobacz [porady: pobieranie informacji o ciągu kwerendy w aplikacji ClickOnce w trybie Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Nigdy nie należy przekazywać argumentów odebranych za pośrednictwem ciągu zapytania do bazy danych lub wiersza polecenia bez sprawdzenia, czy argumenty są bezpieczne. Argumentami niebezpiecznymi są argumenty zawierające znaki ucieczki bazy danych lub wiersza polecenia, które mogłyby umożliwić złośliwemu użytkownikowi „zmuszenie” aplikacji do wykonywania dowolnie wybranych przez niego poleceń.  
  
> [!NOTE]
>  Argumenty ciągu zapytania są jedynym sposobem, aby przekazać argumenty [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podczas uruchamiania aplikacji. Nie można przekazywać argumenty [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji z poziomu wiersza polecenia.  
  
## <a name="deploying-obfuscated-assemblies"></a>Wdrażanie zestawów zasłoniętych  
 Visual Studio zawiera wolnych [cenią sobie wcześniejsze ochrony - Dotfuscator Community Edition](../ide/dotfuscator/index.md), które służy do ochrony aplikacji ClickOnce za pośrednictwem zaciemnienie kodu i środków ochronnych active.  Aby uzyskać więcej informacji, zobacz [sekcji ClickOnce Podręcznik użytkownika Dotfuscator Community Edition](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)