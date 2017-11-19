---
title: "Porady: Określanie deskryptora typu parametru | Dokumentacja firmy Microsoft"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19722a4cffb0e3708939734253b0f2c4a408389e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Porady: określanie deskryptora typu dla parametru
  Deskryptor typu zawiera właściwości opisujące typ danych parametru. Deskryptor typu można zdefiniować pola, jednostki lub kolekcji jednostek. Aby uzyskać więcej informacji, zobacz [deskryptora typu](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Aby zdefiniować deskryptor typu parametru  
  
1.  W **szczegóły metody usługi łączności danych biznesowych** okna, wybierz deskryptor typu parametru.  
  
2.  Na pasku menu wybierz **widoku**, **okna właściwości**.  
  
3.  W **właściwości** Ustaw właściwości deskryptor typu.  
  
     Poniższe procedury opisują sposób definiowania deskryptor typu jako kolekcja pola, jednostki lub jednostek.  
  
### <a name="to-define-a-field"></a>Aby zdefiniować pole  
  
1.  W **właściwości** ustaw **nazwa** właściwości deskryptora typu na nazwę pola w typie, który reprezentuje jednostkę (na przykład: **imię**).  
  
2.  Na liście dalej, aby **TypeName** właściwości, wybierz odpowiedni typ danych (na przykład **Int32**).  
  
     Informacje o innych parametrach opcjonalnych, zobacz [deskryptora typu](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-an-entity"></a>Aby zdefiniować jednostki  
  
1.  W **właściwości** ustaw **nazwa** nazwę opisującą jednostki dla właściwości (na przykład: **skontaktuj się z**).  
  
2.  Ustaw **TypeName** właściwość, aby w pełni kwalifikowana nazwa typu, który reprezentuje jednostkę. Tego typu może być klasę w projekcie, typ zdefiniowany w zestawie, do którego odwołuje się rozwiązania lub typem zdefiniowanym w modelu BDC obiektu.  
  
    -   Dla klasy w projekcie, wybierz strzałkę w dół **TypeName** właściwości, wybierz **bieżącego projektu** karty w oknie dialogowym zostanie wyświetlona, a następnie wybierz klasę w projekcie.  
  
         W pełni kwalifikowana nazwa zawiera przestrzeń nazw i nazwę klasy następuje nazwa systemu LOB. W poniższym przykładzie ustawiono wartość **TypeName** właściwości klasy w projekcie.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Dla typu znajduje się w zestawie rozwiązania w pełni kwalifikowana nazwa zawiera nazwę typu, nazwę zestawu, numer wersji, kulturę i token klucza publicznego.  
  
         W poniższym przykładzie ustawiono wartość **TypeName** właściwości Typ zdefiniowany w zestawie, do którego odwołuje się rozwiązania.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Dla typu zdefiniowanego w modelu obiektu usługi łączności danych biznesowych w pełni kwalifikowana nazwa zawiera przestrzeń nazw i nazwę typu.  
  
         W poniższym przykładzie ustawiono wartość **TypeName** właściwość do typu w modelu BDC obiektu.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  W **szczegóły metody usługi łączności danych biznesowych** okna, Otwórz na liście dla deskryptora typu, a następnie wybierz **Edytuj**.  
  
     **Eksplorator modelu BDC** zostanie otwarte okno.  
  
4.  W **Eksplorator modelu BDC**, otwórz menu skrótów deskryptora typu, a następnie wybierz **dodać deskryptor typu**.  
  
     Nowy deskryptor typu jest dodawana jako element podrzędny do deskryptora typu jednostki. Skonfiguruj ten deskryptor typu jako pola.  
  
5.  Powtórz krok 4, aby dodać podrzędne deskryptor typu dla każdego pola jednostki.  
  
### <a name="to-define-a-collection-of-entities"></a>Aby zdefiniować kolekcji jednostek  
  
1.  W **szczegóły metody usługi łączności danych biznesowych** okna, deskryptor typu parametru, który chcesz wybrać.  
  
2.  Na pasku menu wybierz **widoku**, **okna właściwości**.  
  
3.  W **właściwości** ustaw **nazwa** nazwę opisującą jednostki dla właściwości (na przykład: **kontaktów**).  
  
4.  Ustaw **IsCollection** właściwości **True**. Oznacza to, że ten deskryptor typu jest kolekcji jednostek.  
  
5.  Ustaw **TypeName** właściwości na ciąg, który zawiera odwołanie do <xref:System.Collections.Generic.IEnumerable%601> interfejsu i w pełni kwalifikowana nazwa typu, który reprezentuje jednostkę. Tego typu może być klasę w projekcie, typ zdefiniowany w zestawie, do którego odwołuje się rozwiązania lub typem zdefiniowanym w modelu BDC obiektu.  
  
    -   Dla klasy w projekcie, wybierz strzałkę w dół **TypeName** właściwości, wybierz **bieżącego projektu** karty w oknie dialogowym zostanie wyświetlona, a następnie wybierz klasę w projekcie.  
  
         W pełni kwalifikowana nazwa zawiera przestrzeń nazw i nazwę klasy następuje nazwa systemu LOB.  
  
         W poniższym przykładzie ustawiono wartość **TypeName** właściwości do kolekcji klas w projekcie.  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` ` BdcModel1.Contact, BdcModel1] "  
  
    -   Dla typu znajduje się w zestawie rozwiązania w pełni kwalifikowana nazwa zawiera nazwę typu, nazwę zestawu, numer wersji, kulturę i token klucza publicznego.  
  
         W poniższym przykładzie ustawiono wartość **TypeName** właściwości w kolekcji typów w zestawie, do którego odwołuje się rozwiązania.  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, wersja = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089] "  
  
    -   Dla typu zdefiniowanego w modelu obiektu usługi łączności danych biznesowych w pełni kwalifikowana nazwa zawiera tylko przestrzeń nazw i nazwę typu.  
  
         W poniższym przykładzie ustawiono wartość **TypeName** właściwości w kolekcji typów zdefiniowanych w modelu BDC obiektu.  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType] "  
  
6.  W **szczegóły metody usługi łączności danych biznesowych** okna, Otwórz na liście dla deskryptora typu, a następnie wybierz **Edytuj**.  
  
     **Eksplorator modelu BDC** zostanie otwarte okno.  
  
7.  W **Eksplorator modelu BDC**, otwórz menu skrótów deskryptora typu, a następnie wybierz **dodać deskryptor typu**.  
  
     Nowy deskryptor typu jest dodawana jako element podrzędny do deskryptora typu kolekcji. Skonfiguruj ten deskryptor typu jako jednostki.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Porady: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Porady: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Porady: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  