---
title: 'Porady: Lokalizowanie funkcji | Dokumentacja firmy Microsoft'
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
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53dbaa806ae3b65314d5aeed8df9338905a946cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-localize-a-feature"></a>Porady: lokalizowanie funkcji
  Domyślnie funkcja tytuły i opisy używają wartości ciągu ustalony. Do zlokalizowania funkcji tytuł i opis, Zastąp ciągi wyrażeń, które odwołują się zlokalizowanych zasobów.  
  
## <a name="localizing-a-feature"></a>Lokalizowanie funkcji  
  
#### <a name="to-localize-a-feature"></a>Aby lokalizowanie funkcji  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **Feature1** węzeł, a następnie wybierz pozycję **dodawania zasobów funkcji**.  
  
2.  W **dodawania zasobów** okno dialogowe Wybierz **Język niezmienny** na liście jako kulturę używaną do pliku zasobów funkcji języka domyślnego.  
  
3.  Powtórz poprzedni krok dla każdego z języków lokalizacji, Wybieranie języków wybranych przez użytkownika dla funkcji zlokalizowanych plików zasobów.  
  
     Tworzone są pliki zasobów osobnych funkcji: jeden język domyślny i jeden dla każdego zlokalizowanego języka, które mają być obsługiwane.  
  
4.  Otwórz każdy plik zasobu w edytorze zasobów, a następnie wprowadź wszystkie identyfikatory ciągów i ich wartości.  
  
     Na przykład w pliku zasobów funkcji domyślny, wprowadź identyfikator ciągu **tytuł** o wartości **Mój tytuł funkcji**, a drugi ciąg Identyfikatora **opis** o wartości **Mój opis funkcji**. Dla każdego pliku zlokalizowanych zasobów Użyj tych samych parametrach identyfikatory używane w zasobie funkcji domyślny, ale wprowadź zlokalizowanych ciągów dla wartości.  
  
5.  Po wprowadzeniu wszystkich wartości zasobów, otwórz menu skrótów dla funkcji (na przykład Feature1.feature), a następnie wybierz **Widok projektanta** otworzyć funkcję w Projektancie funkcji.  
  
6.  Aby zlokalizować **tytuł** i **opis** pól w funkcję, użyj następującego formatu, aby wprowadzić wartości w polach ich:  
  
     `$Resources:`*Identyfikator ciągu*  
  
     Na przykład wprowadź $Resources:**tytuł** w **nazwa funkcji** pole i $Resources:**opis** w **opis funkcji** pole .  
  
     Ciąg identyfikatory muszą być zgodne te, które są używane w plikach zasobów.  
  
7.  Wybierz klawisz F5, aby skompilować i uruchomić aplikację.  
  
8.  W programie SharePoint, należy otworzyć **Akcje witryny** menu, wybierz **ustawienia lokacji**, a następnie w **Akcje witryny** wybierz **Zarządzanie funkcji witryny** łącza.  
  
9. W programie SharePoint zmień język wyświetlania domyślnego.  
  
     Funkcja zlokalizowane tytuły i opisy są wyświetlane w aplikacji. Aby wyświetlić zlokalizowanych zasobów, serwer programu SharePoint musi mieć zainstalowany pakiet językowy zgodny plik zasobu kultury.  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Porady: Dodawanie pliku zasobów](../sharepoint/how-to-add-a-resource-file.md)   
 [Porady: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Porady: Lokalizowanie kodu](../sharepoint/how-to-localize-code.md)  
  
  