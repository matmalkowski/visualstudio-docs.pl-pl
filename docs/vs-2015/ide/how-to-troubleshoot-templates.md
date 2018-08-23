---
title: 'Porady: Rozwiązywanie problemów z szablonami | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b249fe28f91a8dfb24e73ab86f785103910ee9d9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677961"
---
# <a name="how-to-troubleshoot-templates"></a>Porady: rozwiązywanie problemów z szablonami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Rozwiązywanie problemów z szablonami](https://docs.microsoft.com/visualstudio/ide/how-to-troubleshoot-templates).  
  
Jeśli szablon nie są ładowane w środowisku deweloperskim, istnieją zlokalizowania problemu na kilka sposobów.  
  
## <a name="validating-the-vstemplate-file"></a>Sprawdzanie poprawności pliku .vstemplate  
 Jeśli plik .vstemplate w szablonie nie pasuje do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] schemat szablonu, szablon nie może występować w **nowy projekt** okno dialogowe.  
  
#### <a name="to-validate-the-vstemplate-file"></a>Aby sprawdzić poprawność pliku .vstemplate  
  
1.  Zlokalizuj plik .zip zawierający szablon.  
  
2.  Wyodrębnij plik zip.  
  
3.  Na **pliku** menu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kliknij przycisk **Otwórz**, a następnie kliknij przycisk **pliku**.  
  
4.  Wybierz plik .vstemplate szablonu, a następnie kliknij przycisk **Otwórz**.  
  
5.  Sprawdź, czy kod XML w pliku .vstemplate działa zgodnie z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] schemat szablonu. Aby uzyskać więcej informacji na temat schematu .vstemplate, zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
    > [!NOTE]
    >  Aby uzyskać obsługę technologii IntelliSense podczas tworzenia pliku .vstemplate, Dodaj `xmlns` atrybutu `VSTemplate` elementu i przypisz jej wartość http://schemas.microsoft.com/developer/vstemplate/2005.  
  
6.  Zapisz i zamknij plik .vstemplate.  
  
7.  Wybierz pliki zawarte w szablonie, kliknij prawym przyciskiem myszy, wybierz opcję **Wyślij do**i kliknij przycisk **skompresowany Folder (zip)**. Wybrane pliki są kompresowane w pliku zip.  
  
8.  W tym samym katalogu co stary plik zip, należy umieścić nowy plik zip.  
  
9. Usuń pliki szablonów wyodrębniony i stary plik zip szablonu.  
  
## <a name="monitoring-the-event-log"></a>Monitorowanie dziennika zdarzeń  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dzienniki błędów napotkanych podczas przetwarzania plików zip szablonu. Jeśli szablon nie jest wyświetlany w **nowy projekt** okno dialogowe jako oczekiwana, możesz użyć **Podgląd zdarzeń** Aby rozwiązać ten problem.  
  
#### <a name="to-locate-template-errors-in-event-viewer"></a>Aby znaleźć błędy szablonu w Podglądzie zdarzeń  
  
1.  W Windows, kliknij przycisk **Start**, kliknij przycisk **Panelu sterowania**, kliknij dwukrotnie **narzędzia administracyjne**, a następnie kliknij dwukrotnie **Podgląd zdarzeń**.  
  
2.  W okienku po lewej stronie kliknij **aplikacji**.  
  
3.  Wyszukaj zdarzenia z **źródła** wartość `Visual Studio - VsTemplate`.  
  
4.  Kliknij dwukrotnie zdarzenie szablonu, aby wyświetlić błąd.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)



