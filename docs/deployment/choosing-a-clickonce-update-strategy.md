---
title: Wybieranie strategii aktualizacji ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: c1099ea3a37491e28929e3452c6364a904aee4d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-a-clickonce-update-strategy"></a>Wybieranie strategii aktualizacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Umożliwia automatyczne stosowanie aktualizacji. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja okresowo odczytuje jej wdrożenia pliku manifestu w celu sprawdzenia, czy aktualizacje aplikacji są dostępne. Jeśli są dostępne, jest pobierana i uruchamiana nowa wersja aplikacji. W celu zwiększenia wydajności pobierane są tylko pliki, które uległy zmianie.  
  
 Podczas projektowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, należy określić strategii, która aplikacja będzie używać do sprawdzania dostępności aktualizacji. Istnieją trzy podstawowe strategie, których można użyć: sprawdzanie, czy są dostępne aktualizacje podczas uruchamiania aplikacji, sprawdzanie, czy są dostępne aktualizacje po uruchomieniu aplikacji (za pomocą wątku działającego w tle) oraz utworzenie interfejsu użytkownika do obsługi aktualizacji.  
  
 Ponadto można określić, jak często aplikacja będzie sprawdzać, czy są dostępne aplikacje, oraz że aktualizacje są wymagane.  
  
> [!NOTE]
>  Aktualizacje aplikacji wymagają łączności sieciowej. W przypadku braku połączenia sieciowego aplikacja zostanie uruchomiona bez sprawdzania, czy są dostępne aktualizacje, niezależnie od wybranej strategii aktualizacji.  
  
> [!NOTE]
>  .NET Framework 2.0 i .NET Framework 3.0, ilekroć kontroli Twojej aplikacji aktualizacji, przed lub po uruchomieniu lub przy użyciu <xref:System.Deployment.Application> interfejsów API, musisz ustawić `deploymentProvider` w manifeście rozmieszczenia. `deploymentProvider` Element odpowiada w programie Visual Studio do **zaktualizować lokalizację** na **aktualizacje** okna dialogowego **publikowania** kartę. Ta reguła przestała obowiązywać w programie .NET Framework 3.5. Aby uzyskać więcej informacji, zobacz [wdrażania ClickOnce aplikacji do testowania i obsługi serwerów produkcyjnych bez Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
## <a name="checking-for-updates-after-application-startup"></a>Sprawdzanie, czy są dostępne aktualizacje, po uruchomieniu aplikacji  
 Gdy jest używana ta strategia, aplikacja będzie podejmować próby zlokalizowania i odczytania pliku manifestu wdrożenia w tle, podczas gdy inne jej funkcje będą normalnie działać. Jeśli będzie dostępna aktualizacja, po następnym uruchomieniu aplikacji użytkownik będzie monitowany o pobranie i zainstalowanie aktualizacji.  
  
 Ta strategia sprawdza się najlepiej w przypadku połączeń sieciowych o niskiej przepustowości lub większych aplikacji, które mogą wymagać pobierania dużych plików.  
  
 Aby włączyć tej strategii aktualizacji, kliknij przycisk **po uruchomieniu aplikacji** w **wybierz, gdy aplikacja ma sprawdzać dostępność aktualizacji** sekcji **aktualizacji aplikacji** okno dialogowe. Następnie określ interwał aktualizacji w sekcji **Określ, jak często aplikacja ma sprawdzać dostępność aktualizacji**.  
  
 Jest to taka sama jak zmiana **aktualizacji** element we wdrożeniu manifestu w następujący sposób:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>Sprawdzanie, czy są dostępne aktualizacje, przed uruchomieniem aplikacji  
 Strategia domyślna polega na próbie zlokalizowania i przeczytania pliku manifestu wdrożenia przed uruchomieniem aplikacji. Gdy jest używana ta strategia, aplikacja będzie podejmować próby zlokalizowania i odczytania pliku manifestu wdrożenia za każdym razem, gdy użytkownik uruchomi aplikację. Jeśli będzie dostępna aktualizacja, zostanie ona pobrana i uruchomiona; w przeciwnym razie zostanie uruchomiona dotychczasowa wersja aplikacji.  
  
 Ta strategia sprawdza się najlepiej w przypadku połączeń sieciowych o wysokiej przepustowości; opóźnienia w uruchamianiu aplikacji mogą być nieakceptowalnie długie w przypadku połączenia o niskiej przepustowości.  
  
 Aby włączyć tej strategii aktualizacji, kliknij przycisk **przed uruchomieniem aplikacji** w **wybierz, gdy aplikacja ma sprawdzać dostępność aktualizacji** sekcji **aktualizacji aplikacji** okno dialogowe.  
  
 Jest to taka sama jak zmiana **aktualizacji** element we wdrożeniu manifestu w następujący sposób:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>Określanie, że aktualizacje są wymagane  
 Możliwe są sytuacje, w których autor aplikacji będzie wymagał, aby użytkownicy używali zaktualizowanej wersji aplikacji. Na przykład może to być spowodowane wprowadzeniem zmian w zasobie zewnętrznym, takim jak usługa sieci Web, które uniemożliwią poprawne działanie wcześniejszych wersji aplikacji. W takim przypadku należy oznaczyć aktualizację jako wymaganą i uniemożliwić użytkownikom uruchamianie wcześniejszych wersji.  
  
> [!NOTE]
>  Sprawdzanie aktualizacji jest wymagany przy użyciu inne strategie aktualizacji, **przed uruchomieniem aplikacji** jest jedynym sposobem zagwarantowania, że nie można uruchomić starszej wersji. Gdy podczas uruchamiania zostanie wykryta obowiązkowa aktualizacja, użytkownik będzie musiał zaakceptować aktualizację lub zamknąć aplikację.  
  
 Aby oznaczyć aktualizacji jako wymagana, kliknij przycisk **określ minimalną wersję wymaganą dla tej aplikacji** w **aktualizacji aplikacji** okna dialogowego, a następnie określ wersji publikowania (**główna**, **Pomocnicza**, **kompilacji**, **poprawki**), który określa najniższy numer wersji aplikacji, która może zostać zainstalowana.  
  
 Jest to taka sama jak ustawienie **parametru minimumRequiredVersion** atrybutu **wdrożenia** elementu w manifeście rozmieszczenia; na przykład:  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>Określanie interwałów aktualizacji  
 Można również określić, jak często aplikacja sprawdza dostępność aktualizacji. W tym celu należy określić, że aplikacja sprawdza dostępność aktualizacji po uruchomieniu, tak jak opisano w sekcji „Sprawdzanie, czy są dostępne aktualizacje, po uruchomieniu aplikacji” wcześniej w tym temacie.  
  
 Aby określić interwał aktualizacji, należy ustawić **Określ, jak często aplikacja ma sprawdzać dostępność aktualizacji** właściwości w **aktualizacji aplikacji** okno dialogowe.  
  
 Jest to taka sama jak ustawienie **maximumAge** i **jednostki** atrybuty **aktualizacji** elementu w manifeście rozmieszczenia.  
  
 Na przykład można chcieć, aby sprawdzanie odbywało się przy każdym uruchomieniu aplikacji, raz w tygodniu lub raz w miesiącu. Jeśli w określonym czasie nie będzie dostępne połączenie z siecią, sprawdzanie dostępności aplikacji zostanie wykonane przy następnym uruchomieniu aplikacji.  
  
## <a name="providing-a-user-interface-for-updates"></a>Dostarczanie interfejsu użytkownika do obsługi aktualizacji  
 Gdy jest używana ta strategia, deweloper aplikacji dostarcza interfejs użytkownika, który umożliwia użytkownikowi określenie, kiedy lub jak często aplikacja ma sprawdzać dostępność aktualizacji. Na przykład można dostarczyć polecenie „Sprawdź, czy są dostępne aktualizacje” albo okno dialogowe „Ustawienia aktualizacji”, w którym będzie można wybrać różne interwały aktualizacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Wdrażania interfejsów API zapewniają struktury programowania z własnego interfejsu użytkownika aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Deployment.Application> przestrzeni nazw.  
  
 Jeśli aplikacja używa interfejsów API wdrożenia do sterowania własną logiką obsługi aktualizacji, należy zablokować sprawdzanie dostępności aktualizacji, tak jak opisano w poniższej sekcji „Blokowanie sprawdzania dostępności aktualizacji”.  
  
 Ta strategia sprawdza się najlepiej w sytuacji, gdy są potrzebne różne strategie aktualizacji dla różnych użytkowników.  
  
## <a name="blocking-update-checking"></a>Blokowanie sprawdzania dostępności aktualizacji  
 Można także spowodować, że aplikacja nigdy nie będzie sprawdzać dostępności aktualizacji. Na przykład może być prostą aplikację, która nigdy nie zostaną zaktualizowane, ale chcesz wykorzystać łatwość instalacji podaj przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.  
  
 Sprawdzanie dostępności aktualizacji warto też zablokować, jeśli aplikacja używa interfejsów API wdrożenia do wykonywania własnych aktualizacji — zobacz sekcję „Dostarczanie interfejsu użytkownika do obsługi aktualizacji” wcześniej w tym temacie.  
  
 Aby zablokować sprawdzania aktualizacji, wyczyść **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru w oknie dialogowym aktualizacji aplikacji.  
  
 Możesz również zablokować aktualizacji sprawdzanie przez usunięcie `<Subscription>` tag w manifeście wdrażania.  
  
## <a name="permission-elevation-and-updates"></a>Podniesienie uprawnień i aktualizacje  
 Jeśli nowa wersja [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja wymaga wyższego poziomu zaufania, aby uruchomić od poprzedniej wersji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pojawi się monit, prośbą, jeśli chce, aby otrzymać wyższy poziom zaufania aplikacji. Jeśli użytkownik odmówi udzielenia wyższego poziomu zaufania, aktualizacja nie zostanie zainstalowana. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pojawi się monit do zainstalowania aplikacji ponownie, po ponownym uruchomieniu dalej. Jeśli użytkownik odmówi w tym punkcie udzielenia wyższego poziomu zaufania, a aktualizacja nie będzie oznaczona jako wymagana, zostanie uruchomiona stara wersja aplikacji. Jeśli jednak aktualizacja będzie wymagana, aplikacja nie zostanie uruchomiona ponownie, dopóki użytkownik nie zaakceptuje wyższego poziomu zaufania.  
  
 Użytkownicy nie będą monitowani o poziomy zaufania w przypadku użycia zaufanego wdrożenia aplikacji. Aby uzyskać więcej informacji, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application>   
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Jak technologia ClickOnce wykonuje aktualizacje aplikacji](../deployment/how-clickonce-performs-application-updates.md)   
 [Instrukcje: zarządzanie aktualizacji dla aplikacji ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)