---
title: 'Porady: sprawdzanie aktualizacji aplikacji, programowo przy użyciu wdrażania interfejsu API ClickOnce | Dokumentacja firmy Microsoft'
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
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ecb3ba8e0fd05e0fb0cd79cde32abe235af743e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633808"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Porady: sprawdzanie aktualizacji aplikacji w sposób programowy za pomocą wdrażania interfejsu API technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Sprawdź aplikacji aktualizacje programowo przy użyciu interfejsu API wdrożenia ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api).  
  
ClickOnce udostępnia dwa sposoby, aby zaktualizować aplikację po jej wdrożeniu. W przypadku pierwszej metody można skonfigurować wdrażania ClickOnce, aby automatycznie sprawdzaj aktualizacje w określonych odstępach czasu. W drugiej metody, można napisać kod, który używa <xref:System.Deployment.Application.ApplicationDeployment> klasy, aby sprawdzał dostępność aktualizacji na podstawie zdarzenia, takie jak żądania użytkownika.  
  
 Poniższe procedury Pokaż kodu umożliwiające wykonywanie aktualizacji programowy i również opis sposobu konfigurowania wdrożenia ClickOnce umożliwia włączenie sprawdzania aktualizacji programowe.  
  
 Aby można było zaktualizować programowo aplikacji ClickOnce, należy określić lokalizację dla aktualizacji. Jest to czasami określane się jako dostawca wdrożenia. Aby uzyskać więcej informacji na temat ustawienia tej właściwości, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Można również użyć techniki opisane poniżej, aby wdrożyć aplikację z jednej lokalizacji, ale została zaktualizowana z innego. Aby uzyskać więcej informacji, zobacz [porady: Określanie alternatywnej lokalizacji aktualizacji wdrażania](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Aby wyszukać aktualizacje programowo  
  
1.  Tworzenie nowej aplikacji Windows Forms przy użyciu preferowanych narzędzi wiersza polecenia lub programu visual.  
  
2.  Utwórz niezależnie od przycisku, element menu lub inny element interfejsu użytkownika ma użytkownikom wybór, aby sprawdzał dostępność aktualizacji. Z tego elementu obsługi zdarzeń należy wywołać następującą metodę, aby wyszukać i zainstalować aktualizacje.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3.  Skompiluj aplikację.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Aby wdrożyć aplikację, która sprawdza, czy aktualizacje programowo przy użyciu Mage.exe  
  
-   Postępuj zgodnie z instrukcjami wdrażania aplikacji za pomocą Mage.exe, jak wyjaśniono w [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Podczas wywoływania Mage.exe do generowania manifestu wdrażania, upewnij się, że należy użyć przełącznika wiersza polecenia `providerUrl`i określ adres URL, w którym technologia ClickOnce będzie sprawdzać aktualizacje. Jeśli aplikacja zostanie zaktualizowana z [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), na przykład, wywołanie do generowania manifestu wdrażania może wyglądać następująco:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Aby wdrożyć aplikację, która sprawdza, czy aktualizacje programowo przy użyciu MageUI.exe  
  
-   Postępuj zgodnie z instrukcjami wdrażania aplikacji za pomocą Mage.exe, jak wyjaśniono w [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Na **opcje wdrażania** kartę, należy ustawić **lokalizacja początkowa** pole manifest aplikacji ClickOnce ma sprawdzać dostępność aktualizacji. Na **opcje aktualizacji** kartę, usuń zaznaczenie **ta aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aplikacja musi mieć uprawnienia pełnego zaufania do korzystania z programowe aktualizowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Określanie alternatywnej lokalizacji aktualizacji wdrażania](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)



