---
title: Lokalizowanie aplikacji ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3d7ebc762c7b1feb895323f7ef9ee0180ce954e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="localizing-clickonce-applications"></a>Lokalizowanie aplikacji ClickOnce
Lokalizacja to proces polegający na wprowadzaniu odpowiednich dla określonej kultury aplikacji. Ten proces obejmuje tłumaczenie tekstu interfejsu użytkownika na język określonego regionu, przy użyciu poprawną datę i formatowanie waluty, dostosowanie rozmiaru formantów w formularzu, i formanty dublowania od prawej do lewej w razie potrzeby.  
  
 Lokalizowanie wyniki aplikacji do tworzenia jeden lub więcej zestawów satelickich. Każdy zestaw zawiera ciągi, obrazy i inne zasoby, które są specyficzne dla danej kultury interfejsu użytkownika. (Aplikacji głównego pliku wykonywalnego zawiera ciągi dla kultury domyślnej aplikacji).  
  
 W tym temacie opisano trzy sposoby wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji dla innych kultur:  
  
-   Dołącz wszystkie zestawy satelickie pojedynczego wdrożenia.  
  
-   Generowanie jednego wdrożenia dla każdego kultury z jednym satelicki zawarte w każdej.  
  
-   Pobieranie zestawów satelickich na żądanie.  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>W przypadku wdrożenia w tym wszystkie zestawy satelickie  
 Zamiast wielu publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, możesz opublikować pojedynczy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, który zawiera wszystkie zestawy satelickie.  
  
 Ta metoda jest ustawieniem domyślnym w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby użyć tej metody w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], nie trzeba wykonywać żadnych dodatkowych działań.  
  
 Aby użyć tej metody z MageUI.exe, należy ustawić kultura dla aplikacji **neutralne** w MageUI.exe. Następnie należy ręcznie dołączyć wszystkie zestawy satelickie w danym wdrożeniu. Zestawy satelickie w MageUI.exe, można dodać za pomocą **wypełnij** znajdującego się na **pliki** kartę manifest aplikacji.  
  
 Zaletą tej metody jest tworzy pojedynczego wdrożenia i upraszcza wątku zlokalizowanych wdrożenia. W czasie wykonywania zestawu satelickiego odpowiednie będzie używany, w zależności od domyślną kulturę użytkownika systemu operacyjnego. Wadą tego podejścia to, że pobiera wszystkie zestawy satelickie zawsze, gdy aplikacja jest zainstalowana lub zaktualizowane na komputerze klienckim. Jeśli aplikacja ma dużą liczbę ciągów lub klienci mają wolne połączenie sieciowe, ten proces może mieć wpływ na wydajność podczas aktualizacji aplikacji.  
  
> [!NOTE]
>  Takie podejście przyjęto założenie, że aplikację można dostosować wysokość, szerokość i położenie formantów automatycznie w celu uwzględnienia rozmiary ciągu inny tekst w innych kultur. Formularze systemu Windows zawiera wiele formantów i technologie, które umożliwiają projektowania formularza, aby był łatwo Lokalizowalny, łącznie z <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel> kontroli, jak również <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.  Zobacz też [porady: Obsługa lokalizacja AutoSize przy użyciu formularzy systemu Windows i formantu TableLayoutPanel](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\)).  
  
## <a name="generate-one-deployment-for-each-culture"></a>Generowanie jednego wdrożenia dla każdego kultury  
 W tej strategii wdrażania generowania wielu wdrożeń. W każdym wdrożeniu obejmują tylko zestawu satelickiego potrzebne dla określonej kultury i Oznacz jako specyficzne dla kultury tego wdrożenia.  
  
 Aby użyć tej metody w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ustaw **publikowania języka** właściwości na **publikowania** kartę do odpowiedniego regionu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zostaną uwzględnione zestawu satelickiego wymagane dla regionu, wybierz i pominie wszystkie zestawy satelickie na wdrożenie.  
  
 To samo można wykonywać za pomocą narzędzia MageUI.exe w programie Microsoft [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Użyj **wypełnij** znajdującego się na **pliki** kartę manifest aplikacji w taki sposób, aby wykluczyć wszystkie zestawy satelickie z katalogu aplikacji, a następnie ustaw **kultury**na **nazwa** kartę manifeście wdrażania w MageUI.exe. Kroki te obejmują nie tylko prawidłowe satelicki, ale także ustawić `language` atrybutu `assemblyIdentity` elementu w manifeście wdrażania do odpowiedniego kultury.  
  
 Po opublikowaniu aplikacji, należy powtórzyć ten krok dla każdego dodatkowego kultury obsługuje Twojej aplikacji. Należy upewnić się, czy publikowania do innego katalogu serwera sieci Web lub katalog udziału pliku zawsze, ponieważ każdy manifest aplikacji będzie odwoływać się do różnych satelicki, a każdy manifest wdrażania będzie mieć inną wartość dla `language`atrybutu.  
  
## <a name="downloading-satellite-assemblies-on-demand"></a>Pobieranie zestawów satelickich na żądanie  
 Jeśli zdecydujesz dołączyć wszystkie zestawy satelickie pojedynczego wdrożenia, może poprawić wydajność przy użyciu pobierania na żądanie, co pozwala na Oznacz zestawy jako opcjonalną. Zestawy oznaczone nie zostaną pobrane, gdy aplikacja jest zainstalowana lub aktualizowane. Można zainstalować zestawy, gdy będziesz potrzebować wywołując <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> metoda <xref:System.Deployment.Application.ApplicationDeployment> klasy.  
  
 Pobieranie zestawów satelickich na żądanie różni się nieco innych typów zestawów na żądanie pobierania. Więcej informacji i kod przykłady dotyczące włączania tego scenariusza za pomocą [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] narzędzi dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], zobacz [wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API wdrażania ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).  
  
 Można również włączyć ten scenariusz w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Zobacz też [wskazówki: Pobieranie zestawów satelickich na żądanie z ClickOnce wdrażania interfejsu API przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) lub [wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API wdrażania ClickOnce Przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>Testowanie zlokalizowanych ClickOnce — aplikacje przed wdrożeniem  
 Zestaw satelicki będzie służyć do formularzy systemu Windows aplikacji tylko wtedy, gdy <xref:System.Threading.Thread.CurrentUICulture%2A> właściwości wątku głównego aplikacji ma ustawioną wartość kultury zestawu satelickiego. Klienci na rynkach lokalnych będzie prawdopodobnie już uruchomiony zlokalizowanej wersji systemu Windows z kulturą, ich odpowiednich domyślną wartość.  
  
 Są trzy opcje do testowania wdrożenia zlokalizowanych przed udostępnieniem aplikacji dla klientów:  
  
-   Można uruchomić Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji na odpowiednim zlokalizowane wersje systemu Windows.  
  
-   Można ustawić <xref:System.Threading.Thread.CurrentUICulture%2A> właściwości w aplikacji. (Ta właściwość musi być ustawiona przed wywołaniem <xref:System.Windows.Forms.Application.Run%2A> metody.)  
  
## <a name="see-also"></a>Zobacz też  
 [\<element assemblyIdentity > — Element](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Globalizacja formularzy Windows Forms](/dotnet/framework/winforms/advanced/globalizing-windows-forms)