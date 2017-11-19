---
title: "Debugowanie aplikacji ClickOnce używających System.Deployment.Application | Dokumentacja firmy Microsoft"
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
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: "14"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 19fa51106512394175159c7dd656badaf583dd3c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Debugowanie aplikacji ClickOnce używających System.Deployment.Application
W [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia można skonfigurować sposób aktualizowania aplikacji. Jednak jeśli chcesz używać i dostosowywanie zaawansowane [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funkcje wdrażania, konieczne będzie dostępu do modelu obiektu wdrożenia podał <xref:System.Deployment.Application>. Można użyć <xref:System.Deployment.Application> interfejsy API dla zaawansowanych zadań, takich jak:  
  
-   Tworzenie opcję "Aktualizuj" w aplikacji  
  
-   Warunkowe, pobieranie na żądanie z różnych składników aplikacji  
  
-   Aktualizacje zintegrowana bezpośrednio w aplikacji  
  
-   Zagwarantowanie, czy aplikacja kliencka jest zawsze aktualny  
  
 Ponieważ <xref:System.Deployment.Application> interfejsów API działa tylko, gdy aplikacja jest wdrażana z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologii, jedynym sposobem na ich debugowania jest wdrożenie aplikacji przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], Dołącz do niego, a następnie jego debugowania. Może być trudne można dołączyć debugera wystarczająco, wczesne, ponieważ ten kod jest często uruchamiany, gdy aplikacja jest uruchamiany i wykonuje przed można uruchomić debugera. Rozwiązaniem jest umieszczenie podziały (lub zatrzymuje dla projektów języka Visual Basic) przed z kodu sprawdzania aktualizacji lub kodu na żądanie.  
  
 Zalecana metoda debugowania jest następujący:  
  
1.  Przed rozpoczęciem upewnij się, że symboli (.pdb) i pliki źródłowe zostaną zarchiwizowane.  
  
2.  Wdrażanie aplikacji w wersji 1.  
  
3.  Utwórz nowe puste rozwiązanie. Z **pliku** menu, kliknij przycisk **nowy**, następnie **projektu**. W **nowy projekt** po otwarciu okna dialogowego **inne typy projektów** węzła, następnie wybierz **rozwiązań programu Visual Studio** folderu. W **szablony** okienku wybierz **puste rozwiązanie**.  
  
4.  Dodaj lokalizację źródłową zarchiwizowane do właściwości dla tego nowego rozwiązania. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, a następnie kliknij przycisk **właściwości**. W **strony właściwości** okno dialogowe, wybierz opcję **debugowania plików źródłowych**, następnie dodać katalog kodu źródłowego zarchiwizowane. W przeciwnym razie debuger znajdzie pliki źródłowe nieaktualne, ponieważ ścieżki pliku źródłowego są rejestrowane w pliku PDB. Jeśli debuger używa plików źródłowych nieaktualne, zobaczysz komunikat informujący, że źródło nie jest zgodny.  
  
5.  Upewnij się, że debuger można znaleźć pliku PDB. Jeśli wdrożono je z aplikacją, debuger znajdzie je automatycznie. Zawsze szuka obok zestawu zagrożona najpierw. W przeciwnym razie należy dodać ścieżkę archiwum do **symboli (.pdb) lokalizacje** (dostęp do tej opcji z **narzędzia** menu, kliknij przycisk **opcje**, następnie otwórz  **Debugowanie** węzeł, a następnie kliknij przycisk **symbole**).  
  
6.  Debugowanie, co się stanie, między `CheckForUpdate` i `Download` / `Update` wywołania metody.  
  
     Na przykład że kod może wyglądać następująco:  
  
    ```  
        Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
            If My.Application.Deployment.IsNetworkDeployed Then  
  
                If (My.Application.Deployment.CheckForUpdate()) Then  
  
                    My.Application.Deployment.Update()  
                    Application.Restart()  
  
                End If  
  
            End If  
        End Sub  
    ```  
  
7.  Wdrażanie w wersji 2.  
  
8.  Podjęto próbę dołączenia debugera do aplikacji w wersji 1, ponieważ pobierania aktualizacji w wersji 2. Możesz też użyć `System.Diagnostics.Debugger.Break` metody lub po prostu `Stop` w języku Visual Basic. Oczywiście nie opuszczaj tych wywołań metody w kodzie produkcyjnym.  
  
     Załóżmy na przykład, tworzenia aplikacji formularzy systemu Windows i masz program obsługi zdarzeń dla tej metody za pomocą logika aktualizacji w nim. Do debugowania tego, po prostu Dołącz, zanim przycisk jest naciśnięty, a następnie ustaw punkt przerwania (Upewnij się, że otworzyć odpowiedni plik zarchiwizowanego i ustawić punkt przerwania).  
  
 Użyj <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> właściwości do wywołania <xref:System.Deployment.Application> interfejsów API tylko wtedy, gdy aplikacja jest wdrażana; interfejsy API nie powinna być wywoływana podczas debugowania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application>