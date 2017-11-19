---
title: "Przykładowe rozszerzenie programu Excel: Klasa TechnologyManager | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: "9"
ms.author: douge
manager: douge
ms.openlocfilehash: 1932646809cba6c6211f87965ffee82e918c6882
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="sample-excel-extension-technologymanager-class"></a>Przykładowe rozszerzenie programu Excel: klasa TechnologyManager
Ta klasa rozszerza <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> klasy i udostępnia podstawowe usługi dla [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] rozszerzenia. Chociaż klasa podstawowa ma wiele metod, tylko ich podzbiór jest używana w tym przykładzie.  
  
 W przypadku niektórych metod tylko zwrócić wartość właściwości. Wiele metod mają umożliwiają deweloperom przesłonić domyślny, który algorytmów kompilacji do silnika kodowanego testu interfejsu użytkownika. Te metody throw <xref:System.NotSupportedException> lub zwróć `null`, który informuje platformę, by używać domyślnego algorytmu.  
  
 W zależności od złożoności podstawową technologią tworzenia kodu Menedżera technologii może zająć od kilku tygodni do kilku miesięcy. Program Excel oferuje możliwość utworzenia potencjalnie bardzo dużej technologii menedżera. W tym przykładzie wynosi celowo arkusze programu Excel i komórek i korzysta z ograniczoną formatowania.  
  
 Gdy to możliwe, kod Menedżera technologii używa kanał .NET Remoting otwarty przez `Communicator` klasy do wyodrębnienia informacji z dodatku uruchomionych w procesie programu Excel.  
  
## <a name="com-visibility"></a>Widoczność COM  
 Rozszerzanie powiadomienie, że tej klasy, a każdy element klasy który <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> klasy mają <xref:System.Runtime.InteropServices.ComVisibleAttribute> o wartości `true` klas są widoczne dla modelu COM.  
  
## <a name="technologyname-property"></a>Właściwość TechnologyName  
 To zastąpienie z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> właściwości podaj unikatowy i łatwy do rozpoznania nazwy, która identyfikuje podstawową technologią dla każdego składnika, rozszerzenia. Wartość dla tego rozszerzenia jest "Excel".  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel — metoda  
 To zastąpienie z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> metoda zwraca liczbę wskazującą poziomu wsparcia udostępniające przez Menedżera technologii dla formantu reprezentowany przez podane dojście. Im wyższa wartość zwrócona więcej technologii Menedżera może obsługiwać formantu. W takim przypadku metoda sprawdza okna zawierającego formantu i jeśli arkuszu programu Excel, metoda zwraca największą wartość; w przeciwnym razie zwraca wartość zero, co oznacza, że nie jest obsługiwana.  
  
## <a name="methods-to-get-an-element"></a>Metody w celu uzyskania elementu  
 Istnieje kilka metod ważne, które są używane przez platformę testowanie kodowanego interfejsu użytkownika można pobrać elementu specyficzne dla technologii zapewniając uchwyt punkcie ekranu lub element na podstawie różnych technologii. Kod dla tych metod nie wymaga wyjaśnień. Dostępne są następujące metody podstawowej:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>ParseQueryId — metoda  
 Po utworzeniu kodowanego testu interfejsu użytkownika, użytkownik może określić wartości właściwości dla niektórych lub wszystkich kontrolek w teście. Wartości tych właściwości są używane przez platformę testowania można utworzyć pary nazwa wartość o nazwie właściwości wyszukiwania, które służą do wyszukiwania formantów interfejsu użytkownika określonego podczas testu. Wszystkie właściwości wyszukiwania łącznie stanowią wartość <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> właściwości każdego elementu w technologii, która obejmuje każdego formantu. Ponieważ formant może być konieczne odnaleziono kilka razy podczas testu, ta metoda umożliwia Menedżera technologii zoptymalizować analizowania właściwości wyszukiwania dla danego formantu. Ta metoda zwraca również wartość pliku cookie używanego przez platformę dla kolejnych wyszukiwania dla tego formantu. Ta implementacja metody używa <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> metody, można przeanalizować właściwości wyszukiwania.  
  
## <a name="matchelement-method"></a>MatchElement — metoda  
 Aby wykonać wyszukiwanie sterowania przez Menedżera technologii, można zaimplementować <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> metodę, aby zwracało tablicę pasujących albo zgłosić <xref:System.NotSupportedException>, który informuje platformę, by używać własnej algorytmu wyszukiwania. W obu przypadkach należy zaimplementować <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> metody, których używa tej implementacji ponownie <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> metody.  
  
## <a name="navigation-methods"></a>Metody nawigacji  
 Te metody Pobierz nadrzędnego, elementy podrzędne lub elementów równorzędnych podanego elementu z hierarchii interfejsu użytkownika. Kod jest prosty i wyraźnie komentarze.  
  
## <a name="getexcelelement-internal-method"></a>GetExcelElement wewnętrzny — metoda  
 Ta metoda wewnętrzny uchwytu okna i informacje o elemencie programu Excel i zwraca żądanego elementu programu Excel.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
