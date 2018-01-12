---
title: "Porady: otwieranie rozwiązań pakietu Office bez uruchamiania kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bd7a401ab96cbb196d97b2e210b3ede0a624deb8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Porady: otwieranie rozwiązań pakietu Office bez uruchamiania kodu
  Rozwiązanie Microsoft Office, utworzone za pomocą rozszerzenia kodu zarządzanego jest uruchamiany nawet wtedy, gdy ustawienie zabezpieczeń w aplikacji pakietu Office przez użytkownika końcowego jest ustawiony na wysoki. Jest to spowodowane zabezpieczenie kodu zestawu .NET jest zarządzany przez program Microsoft .NET Framework, nie przez program Microsoft Office.  
  
 Istnieją jednak razy podczas można otworzyć dokumentu bez uruchamiania kodu. Na przykład kod uruchamiany po otwarciu dokumentu może zmienić zawartość, ale chcesz zaktualizować dokument wyglądu przed wprowadzeniem zmian kodu. Warto wysłać dokument o określone informacje w nim osobie lub nie ma kodu do uruchomienia i być może zmienić zawartość.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Istnieje kilka sposobów, aby otworzyć dokument lub skoroszyt zawierający rozszerzenia kodu zarządzanego bez uruchamiania kodu zestawu.  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Aby pominąć zestawu przy użyciu klawisza SHIFT  
  
-   Otwieranie dokumentów i skoroszytów z **pliku** menu, trzymając naciśnięty klawisz SHIFT, aby uniemożliwić wywoływanie zdarzeń inicjowania, podczas otwierania dokumentu programu Word i Excel.  
  
    > [!NOTE]  
    >  Po otwarciu dokumentu lub ze skoroszytu **wprowadzenie** okienka zadań, przytrzymując klawisz SHIFT nie obejścia kod. Ponadto przytrzymując naciśnięty klawisz SHIFT nie zapobiega zdarzenia są zgłaszane po otwarciu dokumentu.  
  
     Ta metoda jest przydatna, jeśli chcesz otworzyć dokument, aby wprowadzić zmiany bez kodu uruchomione i zmienianie najpierw dokumentu.  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Aby pominąć zestawu zmiana nazwy lub usunięcie go  
  
-   Jeśli masz odpowiednie uprawnienia na komputerze, na którym znajduje się zestaw można zmienić nazwy lub Usuń zestaw, dokumentu lub skoroszytu nie można odnaleźć. Powoduje to błąd zgłaszanych w każdym otwarciu dokumentu pakietu Office.  
  
     Jeśli rozwiązania jest używany przez wiele osób, ta metoda uniemożliwia rozwiązanie działa dla wszystkich z nich. Może to być przydatne, jeśli problem został znaleziony w kodzie lub przywoływanego serwera i chcesz zatrzymać wszyscy użytkownicy z jej wykonanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  