---
title: "Powiązanie danych WPF za pomocą LINQ do XML-Przegląd | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b18f5169558067b67795e983e93ca07141ae8be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>Powiązanie danych WPF za pomocą LINQ do XML-Przegląd
W tym temacie przedstawiono funkcje powiązania danych dynamicznych <xref:System.Xml.Linq> przestrzeni nazw. Te funkcje może służyć jako źródło danych dla elementów interfejsu użytkownika w systemie Windows Presentation Foundation (WPF).  
  
## <a name="xaml-and-linq-to-xml"></a>XAML i LINQ do XML  
 Extensible Application Markup Language (XAML) jest dialekt XML utworzone przez firmę Microsoft do obsługi technologii .NET Framework 3.0. Na platformie WPF służy do reprezentowania elementy interfejsu użytkownika i powiązanych funkcji, takich jak zdarzenia i powiązania danych. W systemie Windows Workflow Foundation XAML jest używana do reprezentowania struktura programu, takich jak kontrola programu (*przepływy pracy*). XAML umożliwia deklaratywne aspektów technologii od pokrewne procedurach kod, który definiuje więcej indywidualne zachowanie programu.  
  
 Istnieją dwa sposoby szerokie, współpracujące XAML i LINQ do XML można:  
  
-   Ponieważ XAML pliki są poprawnie sformułowany kod XML, można je było zbadać i manipulować za pomocą XML technologii, takich jak LINQ do XML.  
  
-   Ponieważ LINQ do XML zapytań reprezentuje źródło danych, te zapytania może służyć jako źródło danych dla powiązania danych dla elementów interfejsu użytkownika aplikacji WPF.  
  
 W tej dokumentacji opisano drugi scenariusz.  
  
## <a name="data-binding-in-the-windows-presentation-foundation"></a>Wiązanie danych w systemie Windows Presentation Foundation  
 Powiązanie danych WPF umożliwia elementu interfejsu użytkownika można skojarzyć jedną z właściwości ze źródłem danych. Jest to prosty przykład <xref:System.Windows.Controls.Label> którego tekst przedstawia wartość właściwości publicznej w obiekcie zdefiniowane przez użytkownika. Powiązanie danych WPF opiera się na następujących składników:  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Cel wiązania|Element interfejsu użytkownika, który ma zostać skojarzony ze źródłem danych. Elementy wizualne na platformie WPF pochodzą od <xref:System.Windows.UIElement> klasy.|  
|Właściwość docelowa|*Właściwości zależności* docelowego powiązania, które odzwierciedla wartość źródła danych powiązania. Właściwości zależności są bezpośrednio obsługiwane przez <xref:System.Windows.DependencyObject> klasy, która <xref:System.Windows.UIElement> pochodną.|  
|Powiązania źródła|Obiekt źródłowy dla co najmniej jednej wartości, które są dostarczane do elementu interfejsu użytkownika do prezentacji. WPF automatycznie obsługuje następujące typy jako powiązania źródła: CLR obiekty, obiekty danych ADO.NET, dane XML (od lub LINQ do XML zapytania XPath) lub innego <xref:System.Windows.DependencyObject>.|  
|Ścieżka źródłowa|Właściwość źródła powiązania, który jest rozpoznawany jako wartość lub zbiór wartości, który ma zostać powiązany.|  
  
 Właściwości zależności to pojęcie specyficzne dla WPF reprezentujące dynamicznie obliczona właściwość elementu interfejsu użytkownika. Na przykład właściwości zależności często mają wartości domyślnej lub wartości, które zostały udostępnione przez element nadrzędny. Te właściwości specjalne bazują na wystąpień <xref:System.Windows.DependencyProperty> klasy (i nie pola jako standardowe właściwości). Aby uzyskać więcej informacji, zobacz [Przegląd właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
### <a name="dynamic-data-binding-in-wpf"></a>Powiązanie danych dynamicznych na platformie WPF  
 Domyślnie powiązanie danych występuje tylko wtedy, gdy element docelowy interfejsu użytkownika został zainicjowany. Ta metoda jest wywoływana *jednorazowe* powiązania. W większości przypadków jest to za mało; zwykle rozwiązania wiązania danych wymaga dynamicznie propagowane zmiany w czasie wykonywania przy użyciu jednej z następujących czynności:  
  
-   *Jednokierunkowe* powiązania spowoduje, że zmiany na jednej stronie można automatycznie propagowane. Najczęściej zmiany w źródle są uwzględniane w miejscu docelowym, ale odwrotnej czasami mogą być przydatne.  
  
-   W *dwukierunkowe* powiązanie, zmiany w źródle są automatycznie propagowane do obiektu docelowego, a zmiany z obiektem docelowym są automatycznie propagowane do źródła.  
  
 - Lub dwukierunkowo powiązanie występuje, źródło musisz zaimplementować mechanizm powiadomień zmiany, na przykład zaimplementowanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu lub przy użyciu *PropertyNameChanged* wzorca dla każdej właściwości obsługiwane.  
  
 Aby uzyskać więcej informacji na temat wiązania z danymi na platformie WPF, zobacz [powiązania danych (WPF)](/dotnet/framework/wpf/data/data-binding-wpf).  
  
## <a name="dynamic-properties-in-linq-to-xml-classes"></a>Właściwości dynamicznych w składniku LINQ to XML klas  
 Większość klasy LINQ do XML nie kwalifikuje się jako prawidłowego źródła danych dynamicznych WPF: niektóre z najbardziej przydatne informacje jest dostępna tylko za pośrednictwem metody (i nie właściwości) i właściwości w tych klas nie implementują powiadomienia o zmianie. Aby obsługuje powiązanie danych WPF, LINQ do XML udostępnia zestaw *właściwości dynamicznych*.  
  
 Te właściwości dynamicznych są specjalne właściwości środowiska wykonawczego, które powielają funkcjonalność istniejących metod i właściwości w <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> klasy. Zostały one dodane do tych klas wyłącznie w celu umożliwienia im na działanie jako źródła danych dynamicznych dla WPF. Aby spełnić te wymagania, te właściwości dynamicznych implementuje powiadomienia o zmianie. Odwołania do szczegółowych dla tych właściwości dynamicznych znajduje się w następnej sekcji [LINQ do XML właściwości dynamicznych](../designers/linq-to-xml-dynamic-properties.md).  
  
> [!NOTE]
>  Znaleziono wiele standardowe właściwości publicznej, w różnych klas w <xref:System.Xml.Linq> przestrzeni nazw może służyć do wiązania danych jednorazowego. Należy jednak pamiętać, że źródło ani elementem docelowym będzie dynamicznie zaktualizowane zgodnie z tym systemem.  
  
### <a name="accessing-dynamic-properties"></a>Uzyskiwanie dostępu do właściwości dynamicznych  
 Właściwości dynamicznych w <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> jak standardowe właściwości nie można uzyskać dostępu do klasy. Na przykład w zgodne CLR języków, takich jak C#, ich nie może być:  
  
-   Dostępne bezpośrednio w czasie kompilacji. Właściwości dynamiczne są niewidoczne, kompilatora i Visual Studio IntelliSense.  
  
-   Wykrytych lub używanych w czasie wykonywania za pomocą odbicia .NET. Nawet w czasie wykonywania nie są one właściwości w tym sensie, podstawowe CLR.  
  
 W języku C#, właściwości dynamicznych można uzyskać tylko w czasie wykonywania za pośrednictwem przez <xref:System.ComponentModel> przestrzeni nazw.  
  
 Z kolei jednak w formacie XML źródła właściwości dynamicznych jest możliwy za pośrednictwem prostego notacji w następującym formacie:  
  
```  
<object>.<dynamic-property>  
```  
  
 Właściwości dynamiczne, które dla tych dwóch klas albo rozpoznana jako wartość, której można użyć bezpośrednio, lub indeksator musi być zasilane indeksu w celu uzyskania wartości wynikowej lub zbiór wartości. Ostatnie składni ma postać:  
  
```  
<object>.<dynamic-property>[<index-value>]  
```  
  
 Aby uzyskać więcej informacji, zobacz [LINQ do XML właściwości dynamicznych](../designers/linq-to-xml-dynamic-properties.md).  
  
 Aby zaimplementować wiązania dynamicznego WPF, właściwości dynamicznych będą używane z przez <xref:System.Windows.Data> przestrzeni nazw, głównie <xref:System.Windows.Data.Binding> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych WPF za pomocą LINQ do XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [LINQ do XML właściwości dynamicznych](../designers/linq-to-xml-dynamic-properties.md)   
 [XAML w WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)   
 [Powiązanie (WPF) danych](/dotnet/framework/wpf/data/data-binding-wpf)   
 [Przy użyciu znaczników przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=98685)