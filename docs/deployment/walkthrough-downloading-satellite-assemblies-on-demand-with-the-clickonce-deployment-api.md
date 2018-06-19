---
title: 'Wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b686feb370ff522b2b26866990cc8069b465d96
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561379"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Wskazówki: pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce
Dla wielu kultur przy użyciu zestawów satelickich można skonfigurować aplikacji formularzy systemu Windows. A *zestawu satelickiego* jest zestawu zawierającego zasoby aplikacji dla kultury innej niż aplikacja domyślna kultura.  
  
 Zgodnie z opisem w [lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md), może zawierać wiele zestawów satelickich dla wielu kultur w tym samym [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Domyślnie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pobierze wszystkie zestawy satelickie w danym wdrożeniu do komputera klienckiego, chociaż jednego klienta, prawdopodobnie będzie wymagać zestawu satelickiego tylko jeden.  
  
 W tym przewodniku pokazano, jak oznaczyć ponownie zestawy satelickie jako opcjonalne i pobierania zestawu, komputer kliencki musi uzyskać bieżące ustawienia kultury. W poniższej procedurze użyto narzędzi dostępnych w ramach [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Można również wykonać tego zadania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Zobacz też [wskazówki: Pobieranie zestawów satelickich na żądanie z ClickOnce wdrażania interfejsu API przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) lub [wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API wdrażania ClickOnce Przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  Do celów testowych, w poniższym przykładzie kodu programowo ustawia kulturę `ja-JP`. Zobacz sekcję "Czynności" w dalszej części tego tematu zawiera informacje na temat sposobu Dostosuj ten kod w środowisku produkcyjnym.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że wiesz, jak dodać zlokalizowanych zasobów do aplikacji przy użyciu programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](https://msdn.microsoft.com/en-us/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Aby pobrać zestawów satelickich na żądanie  
  
1.  Dodaj następujący kod do aplikacji, aby umożliwić pobieranie zestawów satelickich na żądanie.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2.  Generowanie zestawów satelickich dla aplikacji za pomocą [Resgen.exe (Generator pliku zasobów)](/dotnet/framework/tools/resgen-exe-resource-file-generator) lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Generuj manifest aplikacji, lub Otwórz istniejący manifest aplikacji, za pomocą MageUI.exe. Aby uzyskać więcej informacji o tym narzędziu, zobacz [MageUI.exe (Generowanie manifestu i edytowania narzędzia graficzne klienta)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
4.  Kliknij przycisk **pliki** kartę.  
  
5.  Kliknij przycisk **wielokropka** przycisk (**...** ) i wybierz katalog zawierający zestawy i pliki, w tym zestawy satelickie wygenerowanych przy użyciu Resgen.exe aplikacji. (Zestawu satelickiego mają nazwy w postaci *isoCode*\ApplicationName.resources.dll, gdzie *isoCode* to identyfikator języka w formacie RFC 1766.)  
  
6.  Kliknij przycisk **wypełnij** Aby dodać pliki do wdrożenia.  
  
7.  Wybierz **opcjonalnie** pole wyboru dla każdego zestawu satelickiego.  
  
8.  Ustaw pole grupy dla każdego zestawu satelickiego do jego identyfikator języka ISO. Na przykład dla zestawu satelickiego japońskim, należy określić nazwę grupy pobierania `ja-JP`. Spowoduje to włączenie kodzie dodanym w kroku 1, aby pobrać zestawu satelickiego odpowiednie, w zależności od użytkownika <xref:System.Threading.Thread.CurrentUICulture%2A> ustawienie właściwości.  
  
## <a name="next-steps"></a>Następne kroki  
 W środowisku produkcyjnym, prawdopodobnie konieczne będzie usunięcie wiersza w przykładzie kodu, który ustawia <xref:System.Threading.Thread.CurrentUICulture%2A> na określoną wartość, ponieważ klient maszyny będą ma poprawną wartość ustawieniem domyślnym. Gdy aplikacja działa na komputerze klienckim japońskim, na przykład <xref:System.Threading.Thread.CurrentUICulture%2A> będzie `ja-JP` domyślnie. Ustawienie tej wartości programowo jest to dobry sposób na test ponownie zestawy satelickie przed wdrożeniem aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)