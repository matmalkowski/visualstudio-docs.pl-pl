---
title: 'Wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: dfd9b73b7cd12108f86f566eb8d1d4a1c3823f4f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633612"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Wskazówki: pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API wdrożenia ClickOnce](https://docs.microsoft.com/visualstudio/deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api).  
  
Aplikacje Windows Forms można skonfigurować dla wielu języków przy użyciu zestawów satelickich. A *zestawie satelickim* to zestaw, który zawiera zasoby aplikacji dla kultury innej niż aplikacja domyślna kultura.  
  
 Zgodnie z opisem w [lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md), może zawierać wiele zestawów satelickich dla różnych kultur, w tym samym [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia. Domyślnie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pobierze wszystkie zestawy satelickie w danym wdrożeniu na komputerze klienckim, mimo że pojedynczego klienta, prawdopodobnie będziesz potrzebować zestawu satelickiego tylko jeden.  
  
 W tym instruktażu pokazano, jak oznaczyć swoje zestawy satelickie jako opcjonalne i Pobierz tylko zestaw na komputerze klienckim musi uzyskać bieżące ustawienia kultury. W poniższej procedurze użyto narzędzi dostępnych w ramach [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Można również wykonać to zadanie w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  Zobacz też [wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu technologii ClickOnce wdrażania interfejsu API przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) lub [wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API wdrożenia ClickOnce Za pomocą projektanta](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  Do celów testowych, w poniższym przykładzie kodu programowo ustawia kulturę `ja-JP`. Zobacz sekcję "Kolejne kroki" w dalszej części tego tematu zawiera informacje na temat dostosować ten kod w środowisku produkcyjnym.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że wiesz, jak dodać zlokalizowane zasoby do aplikacji za pomocą programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Aby pobrać zestawów satelickich na żądanie  
  
1.  Dodaj następujący kod do aplikacji w taki sposób, aby umożliwić pobieranie zestawów satelickich na żądanie.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2.  Generowanie zestawów satelickich dla aplikacji przy użyciu [Resgen.exe (Generator pliku zasobów)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Generuj manifest aplikacji lub Otwórz istniejący manifest aplikacji, za pomocą MageUI.exe. Aby uzyskać więcej informacji o tym narzędziu, zobacz [MageUI.exe (Manifest Generation i graficzny klient Editing Tool)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4.  Kliknij przycisk **pliki** kartę.  
  
5.  Kliknij przycisk **wielokropka** przycisku (**...** ) i wybierz katalog zawierający zestawy aplikacji i plików, w tym zestawy satelickie został wygenerowany przy użyciu Resgen.exe. (Zestawu satelickiego mają nazwy w postaci *isoCode*\ApplicationName.resources.dll, gdzie *isoCode* jest identyfikatorem języka, w formacie RFC 1766.)  
  
6.  Kliknij przycisk **wypełniania** Aby dodać pliki do wdrożenia.  
  
7.  Wybierz **opcjonalnie** pole wyboru obok każdego zestawu satelickiego.  
  
8.  Ustaw pole grupy dla każdego zestawu satelickiego do jego identyfikator języka ISO. Na przykład dla zestawu satelickiego japońskiego, należy określić nazwę grupy pobierania `ja-JP`. Spowoduje to włączenie kodzie dodanym w kroku 1 do pobierania zestawu satelickiego odpowiednie, w zależności od użytkownika <xref:System.Threading.Thread.CurrentUICulture%2A> ustawienie właściwości.  
  
## <a name="next-steps"></a>Następne kroki  
 W środowisku produkcyjnym prawdopodobnie konieczne będzie usunięcie wiersza w przykładzie kodu, który ustawia <xref:System.Threading.Thread.CurrentUICulture%2A> na określoną wartość, ponieważ klient maszyny będą poprawną wartość ustawiono domyślnie. Gdy aplikacja działa na komputerze klienckim japońskiego, na przykład <xref:System.Threading.Thread.CurrentUICulture%2A> będzie `ja-JP` domyślnie. Ustawienie tej wartości programowe jest dobrym sposobem do testowania zestawów satelickich, przed wdrożeniem aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)



