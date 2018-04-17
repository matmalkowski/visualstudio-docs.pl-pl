---
title: 'Wskazówki: Pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce | Dokumentacja firmy Microsoft'
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
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a9dc200d2dbab68dd3cc4577f5024df4077bfc6a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Wskazówki: pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce
Domyślnie wszystkie zestawy zawarte w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zostaną pobrane po pierwszym uruchomieniu aplikacji. Mogą jednak mieć części aplikacji, które są używane przez niewielki zestaw użytkowników. W takim przypadku chcesz pobrać zestawu tylko wtedy, gdy utworzenie jednego z jego typów. Poniższe wskazówki pokazano, jak Oznacz niektóre zestawy w aplikacji jako "opcjonalne", jak pobrać je przy użyciu klasy i w <xref:System.Deployment.Application> przestrzenią nazw, gdy środowisko uruchomieniowe języka wspólnego (CLR) wymaga ich.  
  
> [!NOTE]
>  Aplikacja będzie musiał uruchomić w trybie pełnego zaufania, aby użyć tej procedury.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Można użyć jednego z następujących składników, w tym przewodniku:  
  
-   Zestaw Windows SDK. Zestaw Windows SDK można pobrać z Microsoft Download Center.  
  
-   Program Visual Studio.  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Aby utworzyć projekt, który korzysta z zestawu na żądanie  
  
1.  Utwórz katalog o nazwie ClickOnceOnDemand.  
  
2.  Otwórz okno wiersza polecenia zestawu SDK systemu Windows lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia.  
  
3.  Przejdź do katalogu ClickOnceOnDemand.  
  
4.  Generowanie pary kluczy publiczny/prywatny za pomocą następującego polecenia:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Za pomocą Notatnika lub innego edytora tekstu, zdefiniuj klasę o nazwie `DynamicClass` z jedną właściwość o nazwie `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Zapisz tekst w pliku o nazwie `ClickOnceLibrary.cs` lub `ClickOnceLibrary.vb`, w zależności od języka, można użyć do katalogu ClickOnceOnDemand.  
  
7.  Skompiluj plik do zestawu.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Aby uzyskać token klucza publicznego dla zestawu, użyj następującego polecenia:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Utwórz nowy plik przy użyciu tekstu edytor, a następnie wprowadź poniższy kod. Ten kod tworzy aplikacji formularzy systemu Windows, która pobiera zestawu ClickOnceLibrary, gdy jest to wymagane.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. W kodzie, zlokalizuj wywołanie <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Ustaw`PublicKeyToken` wartości, który został wcześniej pobrany.  
  
12. Zapisz plik jako `Form1.cs` lub `Form1.vb`.  
  
13. Skompiluj go do pliku wykonywalnego przy użyciu następującego polecenia.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Oznaczanie zestawy jako opcjonalne  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Aby oznaczyć zestawy jako opcjonalne w aplikacji ClickOnce za pomocą MageUI.exe  
  
1.  Za pomocą MageUI.exe, Utwórz manifest aplikacji, zgodnie z opisem w [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Użyj następujących ustawień dla manifest aplikacji:  
  
    -   Nazwa manifest aplikacji `ClickOnceOnDemand`.  
  
    -   Na **pliki** strony, w wierszu ClickOnceLibrary.dll ustawić **typ pliku** kolumny **Brak**.  
  
    -   Na **pliki** strony w wierszu ClickOnceLibrary.dll typu `ClickOnceLibrary.dll` w **grupy** kolumny.  
  
2.  Przy użyciu MageUI.exe, tworzenie manifestu wdrożenia, zgodnie z opisem w [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Użyj następujących ustawień dla manifest wdrażania:  
  
    -   Nazwa manifest wdrażania `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Testowanie nowego zestawu  
  
#### <a name="to-test-your-on-demand-assembly"></a>Aby przetestować używanemu zestawowi na żądanie  
  
1.  Przekazywanie z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia na serwerze sieci Web.  
  
2.  Uruchom aplikację z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] z przeglądarki sieci Web, wpisując adres URL do manifestu wdrożenia. Jeśli dzwonisz z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji `ClickOnceOnDemand`i przekaż go do katalogu głównym domeny adatum.com, adres URL będzie wyglądać następująco:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Gdy pojawi się główny formularz, naciśnij klawisz <xref:System.Windows.Forms.Button>. Powinny pojawić się ciąg w oknie okno komunikatu o treści "Hello, World!".  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application.ApplicationDeployment>