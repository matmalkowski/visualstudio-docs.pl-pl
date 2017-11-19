---
title: "Tworzenie aplikacji ClickOnce dla innych użytkowników, aby wdrożyć | Dokumentacja firmy Microsoft"
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
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 0ca5bb824cbe4e37db241aba956f9f6bf91d18cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Tworzenie aplikacji ClickOnce do wdrażania przez inne osoby
Nie wszystkie deweloperów, którzy tworzą wdrożenia ClickOnce planuje wdrożyć same aplikacje. Wiele z nich tylko pakietu aplikacji przy użyciu technologii ClickOnce, a następnie przekazują pliki do klienta, takich jak dużych przedsiębiorstw. Klient staje się odpowiedzialne za hosting aplikacji w swojej sieci. W tym temacie omówiono niektóre problemy związane z takich wdrożeniach w wersjach programu .NET Framework, przed w wersji 3.5. Opisuje nowe rozwiązanie, używając nowej funkcji "używać manifestu dla zaufania" w .NET Framework 3.5. Ponadto zawiera z zalecanych Strategie tworzenia wdrożenia ClickOnce dla klientów, którzy nadal używają starszej wersji programu .NET Framework.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemy związane z tworzeniem wdrożenia dla klientów  
 Pewne problemy występują, jeśli zamierzasz dostarczyć wdrożenia do klienta. Pierwszą kwestią dotyczącą dotyczy podpisywania kodu. Aby można wdrożyć w sieci, manifest rozmieszczenia i aplikacji manifest wdrażania ClickOnce muszą zarówno być podpisane za pomocą certyfikatu cyfrowego. Uruchamia to pytanie, czy ma być używany certyfikat dewelopera lub certyfikat klienta podczas podpisywania manifestów.  
  
 Pytanie o certyfikacie używanym jest krytyczny, ponieważ tożsamość aplikacji ClickOnce jest oparta na podpisu cyfrowego manifestu rozmieszczenia. Jeśli dewelopera podpisuje manifest wdrażania, jeśli klient jest duża firmy, a następnie więcej niż jeden oddziału firmy wdraża dostosowaną wersję aplikacji może prowadzić do konfliktów.  
  
 Załóżmy, że firma Adventure Works ma działu finansowego i działu kadr. Zarówno działów licencji aplikacji ClickOnce firmy Microsoft Corporation, który generuje raporty na podstawie danych przechowywanych w bazie danych SQL. Firma Microsoft dostarcza każdy dział przy użyciu wersji aplikacji, która jest dostosowany do swoich danych. Jeśli aplikacje są podpisane za pomocą tego samego certyfikatu Authenticode, użytkownika, który próbuje użyć obydwu aplikacji napotyka błąd, ponieważ ClickOnce będzie uznawać drugiej aplikacji jest taka sama jak pierwsza. W takim przypadku klient mogą wystąpić nieprzewidywalne i niechcianych efekty uboczne, obejmujących utratę wszystkich danych przechowywanych lokalnie przez aplikację.  
  
 Dodatkowe problem związany, podpisywanie kodu jest `deploymentProvider` elementu w manifeście rozmieszczenia, która wskazuje miejsce wyszukać aktualizacje aplikacji ClickOnce. Ten element ma mają zostać dodane do manifestu wdrożenia przed podpisaniem. Jeśli ten element zostanie dodany później, manifest rozmieszczenia musi być ponownie podpisane.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Wymaganie klienta, aby podpisać Manifest wdrażania  
 Jedno rozwiązanie tego problemu nie jest unikatowa wdrożeń ma znak developer manifest aplikacji, a klient podpisać manifest wdrażania. Gdy ta metoda działa, podaj inne problemy. Ponieważ certyfikatu Authenticode musi pozostać chronionych zasobów, klienta nie można nadać tylko certyfikat do podpisania wdrożenia deweloperów. Gdy klienta może podpisać manifest wdrażania się przy użyciu bezpłatnych narzędzi z zestawu .NET Framework SDK, może to wymagać wiedzy technicznej niż klienta gotowa lub możliwość zapewnienia. W takich przypadkach dewelopera zazwyczaj tworzy aplikację, witryny sieci Web lub inny mechanizm, za pomocą którego klient może przesłać ich wersji aplikacji do podpisywania.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Wpływ klienta logowania zabezpieczeń aplikacji ClickOnce  
 Nawet jeśli projektanta i klienta zgadzają się, że klienta należy zarejestrować manifest aplikacji, szczególnie, ponieważ dotyczy on wdrażanie zaufanej aplikacji to zgłasza inne problemy, które otaczają tożsamości aplikacji. (Aby uzyskać więcej informacji na temat tej funkcji, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).) Załóżmy, że Adventure Works chce skonfigurować jej komputery klienckie, tak aby był uruchamiany z pełnym zaufaniem dowolnej aplikacji udostępniane im przez firmę Microsoft Corporation. Jeśli firma Adventure Works podpisuje manifest wdrażania, ClickOnce zostanie użyty podpisu zabezpieczeń Adventure pracy określić poziom zaufania aplikacji.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Tworzenie wdrożenia klienta przy użyciu Manifest aplikacji dla zaufania  
 ClickOnce w .NET Framework 3.5 zawiera nową funkcję, która umożliwia deweloperom i klienci nowe rozwiązanie do scenariusz jak manifesty powinny być podpisane. Manifest aplikacji ClickOnce obsługuje nowego elementu o nazwie `<useManifestForTrust>` , który umożliwia deweloperom wskazują, że jest podpisu cyfrowego manifestu aplikacji, co powinna być używana do podejmowania decyzji dotyczących zaufania. Deweloper używa narzędzi do tworzenia pakietów ClickOnce — takie jak Mage.exe, MageUI.exe i Visual Studio — umieść ten element w manifeście aplikacji, jak również do osadzania ich nazwa wydawcy i nazwę aplikacji w manifeście.  
  
 Korzystając z `<useManifestForTrust>`, manifest rozmieszczenia nie musi być podpisany za pomocą certyfikatu Authenticode wystawiony przez urząd certyfikacji. Zamiast tego mogą być podpisane przy co nosi nazwę certyfikatu z podpisem własnym. Certyfikatu z podpisem własnym jest generowany przez klienta lub dewelopera przy użyciu standardowych narzędzi zestawu SDK programu .NET Framework, a następnie stosowane do manifestu wdrożenia przy użyciu standardowych narzędzi wdrażania ClickOnce. Aby uzyskać więcej informacji, zobacz [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx).  
  
 Przy użyciu certyfikatu z podpisem własnym dla manifest wdrażania przedstawiono kilka korzyści. Dzięki wyeliminowaniu konieczności dla klienta w celu uzyskania lub utworzyć własne certyfikatu Authenticode `<useManifestForTrust>` upraszcza wdrażanie klienta, umożliwiając developer do obsługi własnych znakowania tożsamości w aplikacji. Wynik jest zestawem podpisem wdrożeń, które są bezpieczniejsze i mają tożsamości aplikacji. Eliminuje to potencjalnych konfliktów, który może wystąpić z wdrożenia tej samej aplikacji do wielu klientów.  
  
 Aby uzyskać szczegółowe informacje o sposobach tworzenia wdrożenia ClickOnce z `<useManifestForTrust>` włączone, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce tego jest nie wymagają Re-Signing i że zachowuje informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Jak aplikacji manifestu dla relacji zaufania działa w czasie wykonywania  
 Aby uzyskać lepsze zrozumienie, jak przy użyciu manifest aplikacji dla relacji zaufania działa w czasie wykonywania, należy wziąć pod uwagę poniższym przykładzie. Aplikacji ClickOnce, przeznaczonego dla programu .NET Framework 3.5 jest utworzone przez firmę Microsoft. Manifest aplikacji używa `<useManifestForTrust>` element i jest podpisany przez firmę Microsoft. Firma Adventure Works podpisuje manifest wdrażania przy użyciu certyfikatu z podpisem własnym. Adventure Works, klienci są skonfigurowani do zaufania wszelkie aplikacje podpisane przez firmę Microsoft.  
  
 Po kliknięciu łącza do manifest wdrażania ClickOnce instaluje aplikację na komputerze użytkownika. Informacje o certyfikacie i wdrożenia zidentyfikować unikatowo aplikacji ClickOnce, na komputerze klienckim. Jeśli użytkownik spróbuje ponownie zainstalować tej samej aplikacji z innej lokalizacji, tej tożsamości ClickOnce można używać do określenia, czy aplikacja już istnieje na komputerze klienckim.  
  
 Następnie ClickOnce sprawdza, czy certyfikat Authenticode, który został użyty do podpisania manifestu aplikacji, który określa poziom zaufania, który przyzna ClickOnce. Ponieważ firma Adventure Works skonfigurował klientom zaufania wszelkie aplikacje podpisane przez firmę Microsoft, tej aplikacji ClickOnce otrzymuje pełne zaufanie. Aby uzyskać więcej informacji, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Tworzenie wdrożenia klienta dla starszych wersji  
 Co zrobić, gdy projektant jest wdrażanie technologii ClickOnce do klientów, którzy korzystają z starsze wersje programu .NET Framework? W poniższych sekcjach podsumowano zalecane rozwiązania, oraz zalety i wady każdego z nich.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Znak wdrożeń w imieniu klienta  
 Jedną ze strategii wdrażania jest przeznaczony dla deweloperów do tworzenia mechanizm do podpisania wdrożeń w imieniu swoich klientów przy użyciu klucza prywatnego przez klienta. Zapobiega to konieczności zarządzania kluczami prywatnymi lub wielu pakietów wdrażania dewelopera. Deweloper zapewnia tylko tego samego wdrożenia do każdego klienta. Jest klienta, aby dostosować go do środowiska za pomocą usługi podpisywania.  
  
 Wadą tej metody jest czasu i kosztów, które są wymagane do zaimplementowania go. Podczas takiej usługi mogą być wbudowane za pomocą narzędzi dostępnych w .NET Framework SDK, spowoduje to dodanie więcej czasu programowanie do cykl życia.  
  
 Jak wspomniano wcześniej w tym temacie, inną wadą jest każdego klienta wersji aplikacji będą tej samej tożsamości aplikacji, co może prowadzić do konfliktów. W przypadku wątpliwości dotyczących dewelopera można zmienić nazwę pola używanego podczas generowania manifestu wdrożenia do nadaj unikatową nazwę każdej aplikacji. Spowoduje to utworzenie oddzielnych tożsamości dla każdej wersji aplikacji i wyeliminować potencjalne konflikty tożsamości. To pole odpowiada `-Name` argumentów dla Mage.exe i do **nazwa** na **nazwa** karty w MageUI.exe.  
  
 Załóżmy, że deweloper utworzył aplikację o nazwie Application1. Zamiast tworzenia pojedynczego wdrożenia z pola Nazwa ustawioną Application1, deweloper może tworzyć wielu wdrożeń z odmianą właściwe dla klienta w tej nazwy, takie jak CustomerA Application1, CustomerB Application1 i tak dalej.  
  
### <a name="deploy-using-a-setup-package"></a>Wdrażanie przy użyciu pakietu instalacyjnego  
 Drugi strategii wdrażania jest generowanie projektu Microsoft Setup wykonywania początkowej wdrażania aplikacji ClickOnce. To może zostać dostarczona w jednym z kilku różnych formatach: jako wdrożenia MSI, jako pliku wykonywalnego konfiguracji (. EXE) lub w pliku cabinet (cab) wraz z skrypt wsadowy.  
  
 Ta technika, deweloper zapewni klienta wdrożenia, który zawiera pliki aplikacji, manifest aplikacji i manifest wdrażania, która służy jako szablon. Klient może działać programu instalacyjnego, który będzie monit o ich dla danego adresu URL wdrożenia (serwer lub lokalizację, z której użytkownicy będą instalować aplikacji ClickOnce udział plików), a także certyfikat cyfrowy. Instalator aplikacji może też z monitem o dodatkowe opcje konfiguracji ClickOnce, takie jak interwał sprawdzania aktualizacji. Po zebraniu informacji Instalatora czy Generuj manifest wdrażania rzeczywistych, podpisz go i publikowania aplikacji ClickOnce do lokalizacji serwera wyznaczonych.  
  
 Istnieją trzy sposoby, że klienta można zarejestrować manifest rozmieszczenia w takiej sytuacji:  
  
1.  Odbiorca może używać certyfikat wystawiony przez urząd certyfikacji (CA).  
  
2.  Zmiany tego podejścia klienta można zarejestrować ich manifest wdrażania z certyfikatu z podpisem własnym. To wadą jest to, że spowoduje aplikacji, które mają być wyświetlane słowa "Nieznany Publisher", gdy użytkownik jest pytany, czy go zainstalować. Korzyścią jest jednak uniemożliwia mniejszych klientów, trzeba poświęcić czas i pieniądze wymagany certyfikat wystawiony przez urząd certyfikacji.  
  
3.  Na koniec deweloper może zawierać własne certyfikatu z podpisem własnym pakiet instalacyjny. Powstaje potencjalne problemy z opisem we wcześniejszej części tego tematu tożsamość aplikacji.  
  
 Wadą metodę ustawienia wdrażania projektu jest wymagane do tworzenia aplikacji niestandardowe wdrożenie wydatków i godzinę.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Mieć klienta Generuj Manifest wdrażania  
 Trzeci strategii wdrażania wyłączeniu do strony tylko pliki aplikacji i manifest aplikacji do klienta. W tym scenariuszu klient jest odpowiedzialny za Generowanie i podpisać manifest wdrażania przy użyciu zestawu .NET Framework SDK.  
  
 Wadą tego rozwiązania jest wymaga klienta, aby zainstalować narzędzia zestawu SDK programu .NET Framework i deweloperów lub administratorem systemu, kto jest doświadczona za ich pomocą. Niektórzy klienci mogą wymagać rozwiązania, które wymaga niewielkiego lub żadnego techniczne z ich strony.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie technologii ClickOnce do testowania i obsługi serwerów produkcyjnych bez ponownego podpisywania](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Wskazówki: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Wskazówki: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)