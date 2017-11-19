---
title: "Porady: sprawdzanie aktualizacji aplikacji programowo przy użyciu wdrażania interfejsu API ClickOnce | Dokumentacja firmy Microsoft"
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
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 9b240bcdcc576e7ace85e766b54e5cd70e4e5503
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Porady: sprawdzanie aktualizacji aplikacji w sposób programowy za pomocą wdrażania interfejsu API technologii ClickOnce
ClickOnce udostępnia dwa sposoby aktualizacji aplikacji po jej wdrożeniu. W metodzie pierwszy można skonfigurować wdrożenie ClickOnce, aby sprawdzał dostępność aktualizacji w określonych odstępach czasu. W drugiej metody, można napisać kod, który używa <xref:System.Deployment.Application.ApplicationDeployment> klasy, aby wyszukać aktualizacje na podstawie zdarzenia, takie jak żądanie użytkownika.  
  
 Poniższe procedury Pokaż kodu do wykonywania aktualizacji programowych i opisano również sposób konfigurowania wdrożenia ClickOnce umożliwia włączenie sprawdzania aktualizacji programowe.  
  
 Aby zaktualizować programowo aplikacji ClickOnce, należy określić lokalizację dla aktualizacji. Jest to czasami określane jako dostawcy rozmieszczenia. Aby uzyskać więcej informacji na temat ustawiania tej właściwości, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Można również użyć techniki opisane poniżej, aby wdrożyć aplikację z jednej lokalizacji, ale została zaktualizowana z innej. Aby uzyskać więcej informacji, zobacz [porady: Określanie alternatywnej lokalizacji aktualizacji wdrażania](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Aby wyszukać aktualizacje programowo  
  
1.  Tworzenie nowej aplikacji formularzy systemu Windows za pomocą programu preferowanych narzędzi wiersza polecenia lub visual.  
  
2.  Utwórz niezależnie od przycisku, element menu lub innego elementu interfejsu użytkownika ma użytkownikom wybór sprawdzanie aktualizacji. Z obsługi zdarzeń dla tego elementu wywołanie następującej metody, aby wyszukać i zainstalować aktualizacje.  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  Kompilowanie aplikacji.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Aby wdrożyć aplikację, która sprawdza, czy aktualizacje programowo przy użyciu Mage.exe  
  
-   Postępuj zgodnie z instrukcjami dotyczącymi wdrażania aplikacji za pomocą Mage.exe zgodnie z objaśnieniem w [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Podczas wywoływania metody Mage.exe Aby wygenerować manifest wdrażania, upewnij się, że przełącznik wiersza polecenia `providerUrl`i określić adres URL, w którym ClickOnce ma sprawdzać dostępność aktualizacji. Jeśli aplikacja zostanie zaktualizowana z [http://www.adatum.com/MyApp](http://www.adatum.com/MyApp), na przykład połączenia, aby wygenerować manifest wdrażania może wyglądać następująco:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Aby wdrożyć aplikację, która sprawdza, czy aktualizacje programowo przy użyciu MageUI.exe  
  
-   Postępuj zgodnie z instrukcjami dotyczącymi wdrażania aplikacji za pomocą Mage.exe zgodnie z objaśnieniem w [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Na **opcje wdrażania** ustaw **Start lokalizacji** pole do manifestu aplikacji ClickOnce ma sprawdzać dostępność aktualizacji. Na **opcje aktualizacji** kartę, wyczyść **ta aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aplikacja musi mieć uprawnienia pełnego zaufania do użycia, aktualizowanie programowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Określanie alternatywnej lokalizacji aktualizacji wdrażania](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)