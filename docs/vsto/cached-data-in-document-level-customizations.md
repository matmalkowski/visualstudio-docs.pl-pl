---
title: Buforowane dane w dostosowaniach na poziomie dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bd93d985b72f945e7a1c70199d6ff3aacf5f0229
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="cached-data-in-document-level-customizations"></a>Buforowane dane w dostosowaniach na poziomie dokumentu
  Podstawowym celem dostosowań na poziome dokumentu jest do oddzielania danych z widoku w dokumentach pakietu Office. Danych odwołuje się do informacji przechowywanych w dokumencie, łącznie z liczb i tekstu. Widok odwołuje się do interfejsu użytkownika i model obiektów programu Microsoft Office Word i Microsoft Office Excel.  
  
 Visual Studio oddziela dane z widoku w dostosowaniach na poziomie dokumentu przez włączenie danych do osadzenia jako *Wyspy danych*, nazywany również *pamięci podręcznej danych*. Mogą odczytywać lub modyfikować dane bezpośrednio bez konieczności uruchamiania programu Word i Excel. Jest to przydatne, gdy należy modyfikować danych w dokumentach na serwerze, który nie ma zainstalowanych w Microsoft Office. Word i Excel są przeznaczone do użytku w środowiskach klienckich; nie są one przeznaczone do uruchomienia na serwerze.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aby uzyskać więcej informacji o dostosowywaniu na poziomie dokumentu, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [architektura dostosowań na poziome dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Zrozumienie modelu programowania dane z pamięci podręcznej  
 Wyspy danych może zawierać dowolny obiekt w rozwiązaniu spełnia określone wymagania. Te obiekty obejmują <xref:System.Data.DataSet> obiektów, <xref:System.Data.DataTable> obiektów, a drugi obiekt, który może być serializowany przez <xref:System.Xml.Serialization.XmlSerializer> klasy. Aby uzyskać więcej informacji, zobacz zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).  
  
 Aby zapewnić buforowane dane widoku, można powiązać formanty formularzy systemu Windows i *hostowania formantów* dokumentu do obiektów w Wyspy danych. Powiązanie danych między Wyspy danych i formanty powiązane z danymi zapewnia dwa synchronizowane. Można również dodać kod sprawdzania poprawności danych, która jest niezależna od formantów. Aby uzyskać więcej informacji, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Formanty hosta zostały rozszerzone wersji obiektów macierzystych w modelach obiektów programu Excel i Word. W przeciwieństwie do obiektów macierzystych kontrolki hosta może być powiązana bezpośrednio do danych zarządzanych obiektów. Aby uzyskać więcej informacji, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md) i [formanty formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Dostęp do pamięci podręcznej danych na serwerze  
 Aby uzyskać dostęp do danych z pamięci podręcznej dokumentu, można użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy. Ta klasa jest częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], i mogą być używane na serwerze bez uruchomionego programu Excel lub Word. Gdy użytkownik otwiera dokument po zmodyfikowaniu pamięci podręcznej danych, wszystkie formanty, które są powiązane z danymi, są automatycznie synchronizowane na zmiany i użytkownik zobaczy zaktualizowanych danych. Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Program Excel i Word nie są wymagane do zapisu danych na serwerze, tylko do wyświetlania na kliencie. Program Excel i Word nawet zbędna, nie można zainstalować na serwerze. Zapewnia to lepszą skalowalność i możliwość wykonywania przetwarzania wsadowego szybkiego dokumentów, które zawierają Wyspy danych.  
  
## <a name="data-caching-for-offline-use"></a>Buforowanie w trybie offline danych  
 Przechowywanie danych w Wyspy danych umożliwia obsługę scenariuszy, w trybie offline. Gdy użytkownik najpierw zostanie otwarty dokument lub do serwera żądanie dokumentu, Wyspy danych jest wypełniony najnowszych danych. Wyspy danych są buforowane w dokumencie i jest dostępna w trybie offline. Użytkownik (i kodu) można manipulować danymi, nawet jeśli żadne połączenie na żywo nie jest dostępna. Gdy użytkownik połączy się ponownie, zmiany w danych można propagowane do źródła danych serwera.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Dane w pamięci podręcznej i porównać niestandardowe elementy XML  
 Niestandardowe elementy XML wprowadzono w programie Microsoft Office system 2007 jako przechowywanie dowolnego fragmentów kodu XML w dokumencie. Niestandardowe elementy XML są przydatne w wielu z tych samych operacji jako pamięci podręcznej danych, istnieją pewne różnice między Wyspy danych i niestandardowe elementy XML. Aby uzyskać więcej informacji na temat niestandardowe elementy XML, zobacz [przegląd części niestandardowy plik XML](../vsto/custom-xml-parts-overview.md).  
  
 W poniższej tabeli wymieniono niektóre różnice i podobieństwa.  
  
||Pamięć podręczna danych|Niestandardowe elementy XML|  
|-|----------------|----------------------|  
|Aplikacje pakietu Office, których można użyć tych?|Dostosowywanie na poziomie dokumentu dla następujących aplikacji:<br /><br /> -Programu Excel<br />-Word|Dokument poziomie aplikacji i rozwiązań dla następujących aplikacji:<br /><br /> -Programu Excel<br />-Programu PowerPoint<br />-Word|  
|Jakie typy danych można przechowywać?|Wszystkie publiczne obiektu w zestawie Twoje dostosowania, który spełnia określone wymagania. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).|Wszystkie dane XML.|  
|Ma dostęp do danych bez uruchamiania aplikacji Microsoft Office?|Tak, przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Tak, korzystając z klas w <xref:System.IO.Packaging> przestrzeni nazw, lub za pomocą Otwórz SDK formatu XML.|  
  
## <a name="see-also"></a>Zobacz także  
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  