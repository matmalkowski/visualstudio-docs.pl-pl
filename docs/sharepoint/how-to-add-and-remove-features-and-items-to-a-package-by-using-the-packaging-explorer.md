---
title: 'Porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dafa11c17968eb5468ecd4eff462ff9474ce5131
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Porady: dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu eksploratora pakietów
  Aby skonfigurować pakiet do wdrożenia SharePoint — elementy i funkcje, można użyć Eksploratora pakietów. SharePoint — elementy projektu i funkcji można dostosować w pliku wsp.  
  
 Alternatywnie można użyć projektanta pakietów do wyświetlania i zmienić kolejność te funkcje, aby zmienić kolejność aktywacji. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="opening-the-packaging-explorer"></a>Otwieranie Eksploratora pakietów  
 Poniższa procedura służy do Otwórz Eksploratora pakietów, jeśli rozwiązanie Visual Studio ma co najmniej jeden projekt programu SharePoint. Alternatywnie Eksploratora pakietów otwierany automatycznie, podczas wyświetlania funkcji lub pakietu projektanta. Po zamknięciu wszystkich funkcji i pakiet projektantów Eksploratora pakietów również zostanie zamknięte.  
  
#### <a name="to-open-the-packaging-explorer"></a>Aby otworzyć Eksploratora pakietów  
  
1.  Na pasku menu wybierz **widoku**, **inne okna**, **Eksploratora pakietów**.  
  
     **Eksploratora pakietów** pojawia się w **przybornika**.  
  
## <a name="adding-a-feature-to-a-package"></a>Dodawanie funkcji do pakietu  
 Można dodać nowych i istniejących funkcji do pakietu przy użyciu Eksploratora pakietów.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Aby dodać funkcję programu SharePoint  
  
1.  Otwórz **Eksploratora pakietów**, otwórz menu skrótów projektu, a następnie wybierz **dodać funkcję**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Aby przenieść istniejące funkcji SharePoint  
  
1.  Otwórz **Eksploratora pakietów**, a następnie wykonaj jedną z następujących czynności:  
  
    -   Przeciągnij **funkcji** z jednego projektu do innego projektu.  
  
    -   Otwórz menu skrótów dla funkcji, wybierz pozycję **Wytnij**, otwórz menu skrótów projektu, do którego chcesz przenieść tę funkcję, a następnie wybierz **Wklej**.  
  
    > [!NOTE]  
    >  Użyj tej procedury, jeśli masz więcej niż jeden projekt programu SharePoint w rozwiązaniu.  
  
## <a name="validating-a-feature-or-package"></a>Sprawdzanie poprawności funkcji lub pakietu  
 Weryfikowanie plików można zidentyfikować potencjalne problemy w funkcji programu SharePoint i pakietów. Ostrzeżenia i błędy są wyświetlane w oknie danych wyjściowych i w oknie Lista błędów.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Aby sprawdzić poprawność funkcji programu SharePoint lub pakietu  
  
1.  Otwórz **Eksploratora pakietów**.  
  
2.  Otwórz menu skrótów dla funkcji lub pakiet, a następnie wybierz pozycję **weryfikacji**.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  