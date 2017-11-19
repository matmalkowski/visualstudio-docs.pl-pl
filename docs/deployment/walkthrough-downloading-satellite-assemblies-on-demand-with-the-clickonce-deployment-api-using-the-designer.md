---
title: "Wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API przy użyciu narzędzia Projektant wdrażania ClickOnce | Dokumentacja firmy Microsoft"
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
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 17a5482afdd56c7393ab791aa2d5ca699c8557b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Wskazówki: pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce za pomocą Projektanta
Dla wielu kultur przy użyciu zestawów satelickich można skonfigurować aplikacji formularzy systemu Windows. A *zestawu satelickiego* jest zestawu zawierającego zasoby aplikacji dla kultury innej niż aplikacja domyślna kultura.  
  
 Zgodnie z opisem w [lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md), może zawierać wiele zestawów satelickich dla wielu kultur w tym samym [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Domyślnie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pobierze wszystkie zestawy satelickie w danym wdrożeniu do komputera klienckiego, chociaż jednego klienta, prawdopodobnie będzie wymagać zestawu satelickiego tylko jeden.  
  
 W tym przewodniku pokazano, jak oznaczyć ponownie zestawy satelickie jako opcjonalne i pobierania zestawu, komputer kliencki musi uzyskać bieżące ustawienia kultury.  
  
> [!NOTE]
>  Do celów testowych, w poniższych przykładach kodu programowo ustawioną kulturą `ja-JP`. Zobacz sekcję "Czynności" w dalszej części tego tematu zawiera informacje na temat sposobu Dostosuj ten kod w środowisku produkcyjnym.  
  
### <a name="to-mark-satellite-assemblies-as-optional"></a>Aby oznaczyć jako opcjonalną zestawy satelickie  
  
1.  Skompilowanie projektu. Spowoduje to wygenerowanie zestawy satelickie dla wszystkich kultur, które są lokalizowanie do.  
  
2.  Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**.  
  
3.  Kliknij przycisk **publikowania** , a następnie kliknij pozycję **pliki aplikacji**.  
  
4.  Wybierz **Pokaż wszystkie pliki** pole wyboru, aby wyświetlić zestawy satelickie. Domyślnie wszystkie zestawy satelickie zostaną uwzględnione w danym wdrożeniu i będą widoczne w tym oknie dialogowym.  
  
     Zestaw satelicki mają nazwy w postaci *isoCode*\ApplicationName.resources.dll, gdzie *isoCode* jest w formacie RFC 1766 identyfikatorem języka.  
  
5.  Kliknij przycisk **nowych...**  w **grupy pobierania** listy dla każdego identyfikatora języka. Po wyświetleniu monitu o podanie nazwy grupy pobierania, wprowadź identyfikator języka. Na przykład dla zestawu satelickiego japońskim, należy określić nazwę grupy pobierania `ja-JP`.  
  
6.  Zamknij **pliki aplikacji** okno dialogowe.  
  
### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Aby pobrać zestawów satelickich na żądanie w języku C# #
  
1.  Otwórz plik Program.cs. Jeśli nie widzisz taki plik w Eksploratorze rozwiązań, wybierz projekt, a na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.  
  
2.  Użyć poniższego kodu do pobrania zestawu satelickiego odpowiednie i uruchomić aplikację.  
  
     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Aby pobrać zestawów satelickich na żądanie w języku Visual Basic  
  
1.  W **właściwości** okna dla aplikacji, kliknij przycisk **aplikacji** kartę.  
  
2.  W dolnej części strony karty, kliknij przycisk **Wyświetl zdarzenia aplikacji**.  
  
3.  Dodaj następujące instrukcje importu na początku pliku ApplicationEvents.VB.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  Dodaj następujący kod do `MyApplication` klasy.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## <a name="next-steps"></a>Następne kroki  
 W środowisku produkcyjnym, prawdopodobnie konieczne będzie usunięcie wiersza w przykładach kodu, które ustawia <xref:System.Threading.Thread.CurrentUICulture%2A> na określoną wartość, ponieważ klient maszyny będą ma poprawną wartość ustawieniem domyślnym. Gdy aplikacja działa na komputerze klienckim japońskim, na przykład <xref:System.Threading.Thread.CurrentUICulture%2A> będzie `ja-JP` domyślnie. Ustawienie jej programowo jest to dobry sposób na test ponownie zestawy satelickie przed wdrożeniem aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)
