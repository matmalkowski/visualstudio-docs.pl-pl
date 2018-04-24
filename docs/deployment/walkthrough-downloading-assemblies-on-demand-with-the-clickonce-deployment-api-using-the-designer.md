---
title: 'Wskazówki: Pobieranie zestawów na żądanie przy użyciu interfejsu API przy użyciu narzędzia Projektant wdrażania ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fef9486f6bbcbea0d330aaf16fe625642f1e662f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Wskazówki: pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce za pomocą Projektanta
Domyślnie wszystkie zestawy są uwzględniane w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zostaną pobrane po pierwszym uruchomieniu aplikacji. Jednak może być części aplikacji, które są używane przez niewielki zestaw użytkowników. W takim przypadku chcesz pobrać zestawu tylko wtedy, gdy utworzenie jednego z jego typów. Poniższe wskazówki pokazano, jak Oznacz niektóre zestawy w aplikacji jako "opcjonalne", jak pobrać je przy użyciu klasy i w <xref:System.Deployment.Application> przestrzenią nazw, gdy środowisko uruchomieniowe języka wspólnego wymaga ich.  
  
> [!NOTE]
>  Aplikacja będzie musiał uruchomić w trybie pełnego zaufania, aby użyć tej procedury.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Aby utworzyć projekt, który używa zestawu na żądanie z programem Visual Studio  
  
1.  Utwórz nowy projekt formularzy systemu Windows w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Na **pliku** menu wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**. Wybierz **biblioteki klas** projektu w oknie dialogowym i nadaj mu nazwę `ClickOnceLibrary`.  
  
    > [!NOTE]
    >  W języku Visual Basic, zaleca się zmodyfikowanie właściwości projektu, aby zmienić głównej przestrzeni nazw dla tego projektu do `Microsoft.Samples.ClickOnceOnDemand` lub do wybranej przestrzeni nazw. Dla uproszczenia dwa projekty w tym przewodniku znajdują się w tej samej przestrzeni nazw.  
  
2.  Zdefiniuj klasę o nazwie `DynamicClass` z jedną właściwość o nazwie `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
3.  Wybierz projekt formularzy systemu Windows w **Eksploratora rozwiązań**. Dodaj odwołanie do <xref:System.Deployment.Application> zestawu i projekt odwołuje się do `ClickOnceLibrary` projektu.  
  
    > [!NOTE]
    >  W języku Visual Basic, zaleca się zmodyfikowanie właściwości projektu, aby zmienić głównej przestrzeni nazw dla tego projektu do `Microsoft.Samples.ClickOnceOnDemand` lub do wybranej przestrzeni nazw. Dla uproszczenia dwa projekty w tym przewodniku znajdują się w tej samej przestrzeni nazw.  
  
4.  Kliknij prawym przyciskiem myszy formularz, kliknij przycisk **kod widoku** z menu i dodaj następujące odwołania do formularza.  
  
     [!code-csharp[ClickOnceOnDemand#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.cs)]
     [!code-vb[ClickOnceOnDemand#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
5.  Dodaj następujący kod, aby pobrać ten zestaw na żądanie. Ten kod przedstawia sposób mapowania zbiór zestawów na nazwę grupy przy użyciu ogólnego <xref:System.Collections.DictionaryBase.Dictionary%2A> klasy. Ponieważ pobierane są tylko jednego zestawu, w tym przewodniku, istnieje tylko jeden zestaw w naszej grupy. W rzeczywistej aplikacji czy może chcesz pobrać wszystkie zestawy związane z funkcją jednej aplikacji w tym samym czasie. W tabeli mapowania pozwala to łatwo zrobić, kojarząc wszystkie biblioteki dll, które należą do funkcji o nazwie grupy pobierania.  
  
     [!code-csharp[ClickOnceOnDemand#2](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.cs)]
     [!code-vb[ClickOnceOnDemand#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
6.  Na **widoku** menu, kliknij przycisk **przybornika**. Przeciągnij <xref:System.Windows.Forms.Button> z **przybornika** na formularzu. Kliknij dwukrotnie przycisk i Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.  
  
     [!code-csharp[ClickOnceOnDemand#3](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.cs)]
     [!code-vb[ClickOnceOnDemand#3](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.vb)]  
  
## <a name="marking-assemblies-as-optional"></a>Oznaczanie zestawy jako opcjonalne  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Aby oznaczyć zestawy jako opcjonalne w aplikacji ClickOnce za pomocą programu Visual Studio  
  
1.  Kliknij prawym przyciskiem myszy projekt formularzy systemu Windows w **Eksploratora rozwiązań** i kliknij przycisk **właściwości**. Wybierz **publikowania** kartę.  
  
2.  Kliknij przycisk **pliki aplikacji** przycisku.  
  
3.  Znajdź na liście ClickOnceLibrary.dll. Ustaw **stan publikowania** pole listy rozwijanej, aby **Include**.  
  
4.  Rozwiń węzeł **grupy** pole rozwijane i wybierz **nowy**. Wprowadź nazwę `ClickOnceLibrary` jako nazwę nowej grupy.  
  
5.  Kontynuować publikowanie aplikacji, zgodnie z opisem w [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Aby oznaczyć zestawy jako opcjonalne w aplikacji ClickOnce za pomocą Generowanie manifestu i edytowania narzędzia — graficznego klienta (MageUI.exe)  
  
1.  Tworzenie sieci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty zgodnie z opisem w [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Przed zamknięciem MageUI.exe, wybierz kartę, która zawiera manifest aplikacji w danym wdrożeniu, a na karcie Wybierz **pliki** kartę.  
  
3.  Znajdź na liście plików aplikacji ClickOnceLibrary.dll i ustawić jej **typ pliku** kolumny **Brak**. Aby uzyskać **grupy** wpisz `ClickOnceLibrary.dll`.  
  
## <a name="testing-the-new-assembly"></a>Testowanie nowego zestawu  
  
#### <a name="to-test-your-on-demand-assembly"></a>Aby przetestować używanemu zestawowi na żądanie  
  
1.  Uruchom aplikację z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Gdy pojawi się główny formularz, naciśnij klawisz <xref:System.Windows.Forms.Button>. Powinny pojawić się ciąg w oknie okno komunikatu o treści "Hello, World!"  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application.ApplicationDeployment>