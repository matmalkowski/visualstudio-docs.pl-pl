---
title: "Tworzenie skojarzenia między jednostkami | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
ms.assetid: c908448c-13d3-4d2f-89ad-8d709b2958fb
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 936832d0db6f71d51d9a415b18e788db2a1e308b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-association-between-entities"></a>Tworzenie skojarzenia między jednostkami
  Można zdefiniować relacji między obiektami modelu łączności danych biznesowych (BDC) przez utworzenie skojarzenia. Program Visual Studio generuje metod, zapewniających konsumentów modelu z informacji na temat każdego skojarzenia. Te metody mogą być używane przez składniki web Part programu SharePoint, listy lub niestandardowych aplikacji, aby wyświetlić relacji danych w interfejsie użytkownika (UI).  
  
## <a name="creating-an-association"></a>Tworzenie skojarzenia  
 Utwórz skojarzenie, wybierając **skojarzenia** sterowania w programie Visual Studio **przybornika**, wybranie pierwszego jednostki (nazywane jednostki źródłowej), a następnie wybierając drugi jednostki (o nazwie jednostki docelowej). Można zdefiniować szczegóły skojarzenia w **Edytor skojarzenia**. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie skojarzenia między jednostkami](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Metody skojarzenia  
 Aplikacje, takie jak składników web Part danych biznesowych programu SharePoint używać skojarzeń przez wywołanie metody w klasie usługi jednostki. Można dodać metody do klasy usługi jednostki, wybierając je w **Edytor skojarzenia**.  
  
 Domyślnie **Edytor skojarzenia** dodaje metodę skojarzenia nawigacji dla jednostek źródłowych i docelowych. Metoda nawigacyjnym stowarzyszenie w jednostce źródłowej umożliwia konsumentów pobrać listę jednostki docelowej. Metoda nawigacji skojarzenia w obiekcie docelowym umożliwia konsumentów do pobierania jednostki źródłowej, które odnoszą się do jednostki docelowej.  
  
 Kod należy dodać do każdej z tych metod, aby uzyskać odpowiednie informacje. Można także dodać inne typy metod w celu obsługi bardziej zaawansowanych scenariuszy. Aby uzyskać więcej informacji na temat każdego z tych metod, zobacz [obsługiwane operacje](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Typy skojarzenia  
 Można tworzyć dwa typy skojarzeń w Projektancie BDC: obcego skojarzenia opartego na kluczach i skojarzenia bez kluczy obcych.  
  
### <a name="foreign-key-based-association"></a>Skojarzenie na podstawie klucza obcego  
 Można utworzyć obcego skojarzenia opartego na kluczach przez dotyczące identyfikatora w jednostce źródłowej na typ deskryptory zdefiniowany w obiekcie docelowym. Ta relacja umożliwia modelu zapewniają rozszerzoną interfejsu użytkownika dla użytkowników. Na przykład formularz w programie Outlook, który umożliwia użytkownikowi utworzenie zamówienia sprzedaży, które można wyświetlić klienci na liście rozwijanej; lub listę zleceń sprzedaży w programie SharePoint, który umożliwia otwarcie strony profilu dla klienta.  
  
 Aby utworzyć skojarzenie na podstawie klucza obcego, dotyczą identyfikatorów i wpisz deskryptory, które mają taką samą nazwę i typ. Na przykład można utworzyć obcego opartego na kluczach skojarzenie między `Contact` jednostki i `SalesOrder` jednostki. `SalesOrder` Jednostki zwraca `ContactID` deskryptor typu jako część parametru zwrotnego metod wyszukiwania lub określonej metody wyszukiwania. Deskryptory obu typów są wyświetlane w **Edytor skojarzenia**. Do utworzenia obcego opartego na kluczach relacji między `Contact` jednostki i `SalesOrder` jednostki, wybierz `ContactID` identyfikator obok każdego z tych pól.  
  
 Dodaj kod do metody Nawigatora skojarzenia jednostki źródłowej, która zwraca kolekcję obiektów docelowego. Poniższy przykład zwraca zamówień kontaktu.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Dodaj kod do metody Nawigatora skojarzenia jednostki docelowej, która zwraca jednostki źródłowej. Poniższy przykład zwraca kontaktu, z którym powiązany jest zamówienia sprzedaży.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Skojarzenie bez kluczy obcych  
 Można utworzyć skojarzenie bez mapowania identyfikatorów deskryptory typ pola. Utwórz skojarzenie tego rodzaju, gdy jednostki źródłowej nie ma bezpośredniej relacji z obiektem docelowym. Na przykład `SalesOrderDetail` tabela nie ma klucza obcego, który jest mapowany na klucz podstawowy w `Contact` tabeli.  
  
 Jeśli chcesz wyświetlić informacje w `SalesOrderDetail` tabeli, która odnosi się do `Contact`, można utworzyć skojarzenie bez kluczy obcych między `Contact` jednostki i `SalesOrderDetail` jednostki.  
  
 W metodzie nawigacyjnym stowarzyszenie `Contact` jednostki zwracanego `SalesOrderDetail` jednostek przez sprzężenie tabel, przez wywołanie procedury składowanej.  
  
 Poniższy przykład zwraca szczegółowe informacje o wszystkich zamówień przez sprzężenie tabel.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 W metodzie nawigacyjnym stowarzyszenie `SalesOrderDetail` jednostki, zwróć pokrewny `Contact`. W poniższym przykładzie pokazano to.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Porady: Tworzenie skojarzenia między jednostkami](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  