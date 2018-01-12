---
title: 'Porady: Lokalizowanie kodu | Dokumentacja firmy Microsoft'
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
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 95c029a7a90283314bdded2a6beeb7f023d7e827
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-localize-code"></a>Porady: lokalizowanie kodu
  Niezlokalizowany kodzie użyto wartości ciągu ustalony. Do localize — ciągi kodu, zastąp je z wywołań <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, czyli metody, która odwołuje się do zlokalizowanych zasobów.  
  
## <a name="localizing-code"></a>Lokalizacja kodu  
  
#### <a name="to-localize-code"></a>Aby lokalizowanie kodu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla elementu projektu, a następnie wybierz **Dodaj**, **modułu**.  
  
     Wybierz **pliku zasobów** szablonu.  
  
    > [!NOTE]  
    >  Pamiętaj dodać pliku zasobu do elementu projektu SharePoint, aby właściwość Typ wdrożenia jest dostępna. Ta właściwość jest wymagana w dalszej części tej procedury.  
  
2.  Nadaj nazwę wybraną dołączany z rozszerzeniem resx, takich jak MyAppResources.resx pliku zasobów języka domyślnego.  
  
3.  Powtórz kroki 1 i 2, aby dodać pliki oddzielnych zasobów do elementu projektu SharePoint: zlokalizowany jednej dla każdego języka.  
  
     Użyj takiej samej nazwie podstawowej dla każdego pliku zlokalizowanych zasobów, ale Dodaj identyfikator kultury. Na przykład nazwę niemieckim zlokalizowany zasób MyAppResources.de DE.resx.  
  
4.  Otwórz każdy plik zasobu i Dodaj zlokalizowanych ciągów. Użyj tych samych parametrach identyfikatorów w każdym pliku.  
  
5.  Zmień wartość **typu wdrożenia** właściwości każdego pliku zasobu do **AppGlobalResource** spowodować każdego pliku wdrożyć folderze App_GlobalResources serwera.  
  
6.  Pozostaw wartość **Akcja kompilacji** właściwość jako **osadzonego zasobu**.  
  
     Zasoby osadzone są kompilowane do projektu biblioteki DLL.  
  
7.  Skompiluj projekt do utworzenia zasobu satelitarne biblioteki dll.  
  
8.  W **projektanta pakietów**, wybierz **zaawansowane** karcie, a następnie dodaj zestawu satelickiego.  
  
9. W **lokalizacji** i dołączy identyfikator kultury folderu na ścieżkę lokalizacji, takich jak de-DE\\*nazwy elementu projektu*. resources.dll.  
  
10. Rozwiązanie nie zawiera już odwołania zestawu System.Web, Dodaj odwołanie do niej i dodanie dyrektywy kod w celu <xref:System.Web>.  
  
11. Znajdź wszystkie ciągi ustalony w kodzie, które są widoczne dla użytkowników, takich jak tekst interfejsu użytkownika, błędy i tekst komunikatu. Zamień wywołanie <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metodę przy użyciu następującej składni:  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Wybierz klawisz F5, aby skompilować i uruchomić aplikację.  
  
13. W programie SharePoint zmień język wyświetlania domyślnego.  
  
     Zlokalizowanych ciągów są wyświetlane w aplikacji. Aby wyświetlić zlokalizowanych zasobów, serwer programu SharePoint musi mieć zainstalowany pakiet językowy zgodny plik zasobu kultury.  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Porady: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md)   
 [Porady: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Instrukcje: Dodawanie pliku zasobu](../sharepoint/how-to-add-a-resource-file.md)  
  
  