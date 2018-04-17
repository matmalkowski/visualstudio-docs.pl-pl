---
title: Wdrażanie rozwiązania do pakietu Office | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a397ef0986bd2a278f4b341dc772c71bc9b0a51
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-an-office-solution"></a>Wdrażanie rozwiązania do pakietu Office
  Rozwiązania dla pakietu Office można wdrażać za technologii ClickOnce lub Instalatora Windows. Funkcja ClickOnce pozwala zmniejszyć liczbę kroków niezbędnych do wdrożenia i aktualizowania rozwiązania. Z kolei Instalator Windows umożliwia pełną kontrolę nad sposobem instalowania rozwiązania oraz doborem stron wyświetlanych przez instalatora podczas instalacji rozwiązania przez użytkowników.  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="deploying-a-solution-by-using-clickonce"></a>Wdrażanie rozwiązania przy użyciu technologii ClickOnce  
 Wdrażanie rozwiązania przy użyciu technologii ClickOnce polega na opublikowaniu go w centralnej lokalizacji, skąd użytkownicy mogą je zainstalować i uruchomić. Rozwiązanie można aktualizować bez konieczności dostarczenia użytkownikom nowego programu instalacyjnego.  Ta opcja wdrażania jest prostsza, ale nie pozwala na przedstawianie użytkownikom stron instalacji niestandardowej. Ponadto rozwiązania trzeba instalować w tylu wystąpieniach, ilu użytkowników korzysta z komputera. Zobacz [wdrażania rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="deploying-a-solution-by-using-windows-installer"></a>Wdrażanie rozwiązania przy użyciu Instalatora Windows  
 Podczas wdrażania rozwiązania przy użyciu Instalatora Windows następuje rozpowszechnienie programu instalacyjnego do użytkowników, którzy następnie sami instalują z niego rozwiązanie. Program instalacyjny może zainstalować rozwiązanie równocześnie dla wszystkich użytkowników komputera, a nie tylko dla bieżącego użytkownika. Oferuje również nieco więcej kontroli nad opcjami wyświetlanymi użytkownikom podczas instalowania rozwiązania. Można na przykład ustawić wyświetlanie umowy licencyjnej albo pozwolić użytkownikom na instalowanie określonych składników rozwiązania. Jednak w przypadku aktualizacji rozwiązania trzeba dostarczyć nowy program instalacyjny. Zobacz [wdrażania rozwiązania do pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Wdrażanie rozwiązania do pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Rozwiązywanie problemów z wdrażaniem rozwiązań Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  