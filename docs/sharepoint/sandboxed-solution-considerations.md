---
title: Zagadnienia dotyczące rozwiązania typu piaskownica | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ff85f3407fb24d6d49856bb11ff1852c544cad35
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sandboxed-solution-considerations"></a>Uwagi dotyczące rozwiązania typu piaskownica
  *Rozwiązania piaskownicy* to funkcja programu Microsoft SharePoint 2010, umożliwiający użytkownikom kolekcji lokacji przekazać swoje własne rozwiązania niestandardowego kodu. Typowe rozwiązania typu piaskownica jest użytkownikom przekazywanie ich własnych składników Web Part.  
  
 Aplikacja trybie piaskownicy programu SharePoint działa w bezpieczny, monitorowanego procesu, który ma dostęp do ograniczonej części kolektywu serwerów sieci Web. Program Microsoft SharePoint 2010 używa kombinacji funkcji, galerie rozwiązania rozwiązanie monitorowania i strukturze weryfikacji, aby umożliwić rozwiązań w trybie piaskownicy.  
  
## <a name="specifying-project-trust-level"></a>Określanie poziomu zaufania projektu  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsługuje rozwiązania w trybie piaskownicy za pośrednictwem właściwości projektu logiczną o nazwie *rozwiązania typu piaskownica*. Tej właściwości można ustawić w dowolnym momencie w projekcie, lub można ją określić podczas tworzenia projektu w **Kreator dostosowania programu SharePoint**.  
  
> [!NOTE]  
>  Zmiana *rozwiązania typu piaskownica* właściwość projektu po jego utworzeniu może spowodować błędy sprawdzania poprawności.  
  
 Rozwiązanie jest brana pod uwagę rozwiązanie z zakresu farmy, jeśli *rozwiązania typu piaskownica* właściwość jest ustawiona na **false** lub możesz wybrać **Wdróż jako rozwiązanie farmy** opcji. Jednak rozwiązanie jest traktowane inaczej niż rozwiązanie farmy Jeśli *rozwiązania typu piaskownica* właściwość jest ustawiona na **true** lub możesz wybrać **Wdróż jako rozwiązanie w trybie piaskownicy** Opcja w kreatorze.  
  
## <a name="sharepoint-site-hierarchy"></a>Hierarchia lokacji programu SharePoint  
 Aby zrozumieć, jak w trybie piaskownicy rozwiązania pracy, warto wiedzieć, witryn programu SharePoint są hierarchiczne w zakresie. Pierwszym elementem nosi nazwę kolektywu serwerów sieci Web i inne elementy są podrzędne w stosunku do niej:  
  
 Kolektywu serwerów sieci Web  
  
 Aplikacja sieci Web A  
  
 Witryna kolekcji A1  
  
 A1a lokacji  
  
 Aplikacja sieci Web B  
  
 B1 kolekcji lokacji  
  
 B1a lokacji  
  
 B1b lokacji  
  
 B2 kolekcji lokacji  
  
 B2a lokacji  
  
 Jak widać, farmy serwerów sieci Web mogą zawierać jedną lub więcej aplikacji sieci Web, które z kolei może zawierać jeden lub więcej zbiory witryn, które mogą mieć Lokacje podrzędne i tak dalej. Zmiany dokonane do jednej lokacji kolekcji potencjalny wpływ tylko zbioru witryn i żaden inny. Jednak zmiany wprowadzone na poziomie farmy sieci Web mają wpływ na wszystkich zbiorach witryn w farmie.  
  
 Windows SharePoint Services (WSS) 3.0 umożliwia wdrażanie rozwiązań tylko na poziomie farmy, ale [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] umożliwia wdrażanie na poziomie farmy (rozwiązanie farmy) lub poziomie zbioru witryn (rozwiązania typu piaskownica).  
  
## <a name="why-sandboxed-solutions"></a>Dlaczego rozwiązań w trybie piaskownicy?  
 3.0 WSS rozwiązania można można wdrożyć tylko na poziomie farmy. Oznacza to, że potencjalnie szkodliwego lub destabilizing rozwiązania mogą być wdrożone dotyczący całej farmy sieci Web i wszystkich zbiorów witryn i aplikacji działających na jego podstawie. Jednak przy użyciu rozwiązań w trybie piaskownicy, można wdrożyć rozwiązanie do obszaru podrzędnego farmy, w określonym zbiorze witryn. Aby zapewnić dodatkową ochronę, zestawu rozwiązania nie został załadowany w głównym [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] procesu (w3wp.exe). Zamiast tego jest ładowany w oddzielnych procesach (SPUCWorkerProcess.exe). Ten proces jest monitorowane i implementuje przydziałów i ograniczania przepustowości do ochrony farmy z rozwiązań w trybie piaskownicy, wykonujących szkodliwych działań, takie jak uruchomienie ścisłej pętle, używające cykli Procesora.  
  
## <a name="site-collection-solution-gallery"></a>Galeria rozwiązania kolekcji witryn  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 jest funkcją, która nazywa się "kolekcji rozwiązania galerii witryn." Możesz korzystać z tej funkcji na stronie Administracja centralna programu SharePoint 2010 lub przez otwarcie **Akcje witryny** menu, wybierając **ustawienia lokacji**, a następnie wybierając **rozwiązań** łącze w obszarze **galerie** w witrynie programu SharePoint. Galerie rozwiązania są repozytoria rozwiązania, które umożliwiają administratorom kolekcji lokacji zarządzanie rozwiązaniami w zbiorach witryn.  
  
 Galeria rozwiązania jest przechowywane w katalogu głównym witryny programu SharePoint w sieci Web biblioteki dokumentów. Galeria rozwiązań zastępuje szablony stron i obsługuje pakietów rozwiązania. Po przekazaniu pliku pakietu (wsp) rozwiązania programu SharePoint jest przetwarzany jako rozwiązanie w trybie piaskownicy.  
  
## <a name="sandboxed-solution-limitations"></a>Ograniczenia dotyczące rozwiązania typu piaskownica  
 Po wdrożeniu rozwiązania typu piaskownica tablicy dostęp do funkcji programu SharePoint jest ograniczony do zmniejszenia wszystkie luki w zabezpieczeniach, które mogą być. Niektóre ograniczenia te obejmują:  
  
-   Rozwiązania piaskownicy ma ograniczony podzestaw elementów możliwych do wdrożenia rozwiązania dostępne dla nich. Potencjalnie narażone szablony projektów programu SharePoint, takich jak witryny definicje i przepływy pracy, nie są dostępne.  
  
-   SharePoint działa kodu rozwiązania w trybie piaskownicy w procesie (SPUCWorkerProcess.exe) niezależnie od głównego [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] procesu (w3wp.exe) puli aplikacji.  
  
-   Nie można dodać katalogi zmapowane do projektu.  
  
-   Typy w [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zestawu Microsoft.Office.Server nie można użyć w trybie piaskownicy rozwiązania. Ponadto tylko typy w [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] zestawu Microsoft.SharePoint mogą być używane w trybie piaskownicy rozwiązania.  
  
 Ważne jest, aby należy pamiętać, tym określenie rozwiązania SharePoint jako rozwiązania typu piaskownica nie ma wpływu na serwer programu SharePoint; Określa tylko wdrażanie projektu programu SharePoint do witryny programu SharePoint z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i jakie zestawy nawiązywania połączenia. Nie ma wpływu na plik wsp wygenerowany i plik wsp nie zawiera danych bezpośrednio skorelowany *rozwiązania typu piaskownica* właściwości.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Możliwości i elementów w trybie piaskownicy rozwiązania  
 Rozwiązania piaskownicy obsługuje następujące funkcje i elementy:  
  
-   Typy zawartości/pola.  
  
-   Niestandardowe akcje  
  
-   Deklaracyjne przepływów pracy  
  
-   Odbiorcy zdarzeń  
  
-   Funkcja objaśnienia  
  
-   Definicje listy  
  
-   Wystąpienia listy  
  
-   Moduł/pliki  
  
-   Nawigacji  
  
-   Onet.XML  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Obsługa wszystkich składników Web Part, które pochodzą z `System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Części sieci Web  
  
-   Elementy funkcji szablonu sieci Web (zamiast Webtemp.xml)  
  
-   Części sieci Web Visual  
  
 Rozwiązania piaskownicy nie obsługują następujące funkcje i elementy:  
  
-   Strony aplikacji  
  
-   Grup akcji niestandardowych  
  
-   Funkcje z zakresu farmy  
  
-   `HideCustomAction` — element  
  
-   Funkcje z zakresu aplikacji sieci Web  
  
-   Przepływy pracy z kodem  
  
## <a name="see-also"></a>Zobacz też  
 [Różnice między rozwiązaniami w trybie piaskownicy oraz rozwiązaniami farmy](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  