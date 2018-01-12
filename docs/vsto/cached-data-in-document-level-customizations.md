---
title: Buforowane dane w dostosowaniach na poziomie dokumentu | Dokumentacja firmy Microsoft
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1fe9465c3f238941ace0d5b6fc438c7d5d93ec64
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="cached-data-in-document-level-customizations"></a>Dane z pamięci podręcznej dostosowywane na poziomie dokumentu
  Podstawowym celem dostosowań na poziome dokumentu jest do oddzielania danych z widoku w dokumentach pakietu Office. Danych odwołuje się do informacji przechowywanych w dokumencie, łącznie z liczb i tekstu. Widok odwołuje się do interfejsu użytkownika i model obiektów programu Microsoft Office Word i Microsoft Office Excel.  
  
 Visual Studio oddziela dane z widoku w dostosowaniach na poziomie dokumentu przez włączenie danych do osadzenia jako *Wyspy danych*, nazywany również *pamięci podręcznej danych*. Mogą odczytywać lub modyfikować dane bezpośrednio bez konieczności uruchamiania programu Word i Excel. Jest to przydatne, gdy należy modyfikować danych w dokumentach na serwerze, który nie ma zainstalowanych w Microsoft Office. Word i Excel są przeznaczone do użytku w środowiskach klienckich; nie są one przeznaczone do uruchomienia na serwerze.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aby uzyskać więcej informacji o dostosowywaniu na poziomie dokumentu, zobacz [rozwój rozwiązań Office ― omówienie &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) i [architektura dostosowań na poziome dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understanding-the-cached-data-programming-model"></a>Omówienie modelu programowania dane z pamięci podręcznej  
 Wyspy danych może zawierać dowolny obiekt w rozwiązaniu spełnia określone wymagania. Te obiekty obejmują <xref:System.Data.DataSet> obiektów, <xref:System.Data.DataTable> obiektów, a drugi obiekt, który może być serializowany przez <xref:System.Xml.Serialization.XmlSerializer> klasy. Aby uzyskać więcej informacji, zobacz zobacz [buforowanie danych](../vsto/caching-data.md).  
  
 Aby zapewnić buforowane dane widoku, można powiązać formanty formularzy systemu Windows i *hostowania formantów* dokumentu do obiektów w Wyspy danych. Powiązanie danych między Wyspy danych i formanty powiązane z danymi zapewnia dwa synchronizowane. Można również dodać kod sprawdzania poprawności danych, która jest niezależna od formantów. Aby uzyskać więcej informacji, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Formanty hosta zostały rozszerzone wersji obiektów macierzystych w modelach obiektów programu Excel i Word. W przeciwieństwie do obiektów macierzystych kontrolki hosta może być powiązana bezpośrednio do danych zarządzanych obiektów. Aby uzyskać więcej informacji, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md) i [formantów formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="accessing-cached-data-on-the-server"></a>Uzyskiwanie dostępu do pamięci podręcznej danych na serwerze  
 Aby uzyskać dostęp do danych z pamięci podręcznej dokumentu, można użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy. Ta klasa jest częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], i mogą być używane na serwerze bez uruchomionego programu Excel lub Word. Gdy użytkownik otwiera dokument po zmodyfikowaniu pamięci podręcznej danych, wszystkie formanty, które są powiązane z danymi, są automatycznie synchronizowane na zmiany i użytkownik zobaczy zaktualizowanych danych. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Program Excel i Word nie są wymagane do zapisu danych na serwerze, tylko do wyświetlania na kliencie. Program Excel i Word nawet zbędna, nie można zainstalować na serwerze. Zapewnia to lepszą skalowalność i możliwość wykonywania przetwarzania wsadowego szybkiego dokumentów, które zawierają Wyspy danych.  
  
## <a name="data-caching-for-offline-use"></a>Buforowanie w trybie Offline danych  
 Przechowywanie danych w Wyspy danych umożliwia obsługę scenariuszy, w trybie offline. Gdy użytkownik najpierw zostanie otwarty dokument lub do serwera żądanie dokumentu, Wyspy danych jest wypełniony najnowszych danych. Wyspy danych są buforowane w dokumencie i jest dostępna w trybie offline. Użytkownik (i kodu) można manipulować danymi, nawet jeśli żadne połączenie na żywo nie jest dostępna. Gdy użytkownik połączy się ponownie, zmiany w danych można propagowane do źródła danych serwera.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Dane w pamięci podręcznej i niestandardowych części XML porównaniu  
 Niestandardowe elementy XML wprowadzono w programie Microsoft Office system 2007 jako przechowywanie dowolnego fragmentów kodu XML w dokumencie. Niestandardowe elementy XML są przydatne w wielu z tych samych operacji jako pamięci podręcznej danych, istnieją pewne różnice między Wyspy danych i niestandardowe elementy XML. Aby uzyskać więcej informacji na temat niestandardowe elementy XML, zobacz [niestandardowych części XML ― omówienie](../vsto/custom-xml-parts-overview.md).  
  
 W poniższej tabeli wymieniono niektóre różnice i podobieństwa.  
  
||Pamięć podręczna danych|Niestandardowe elementy XML|  
|-|----------------|----------------------|  
|Aplikacje pakietu Office, których można użyć tych?|Dostosowywanie na poziomie dokumentu dla następujących aplikacji:<br /><br /> -Programu Excel<br />-Word|Dokument poziomie aplikacji i rozwiązań dla następujących aplikacji:<br /><br /> -Programu Excel<br />-Programu PowerPoint<br />-Word|  
|Jakie typy danych można przechowywać?|Wszystkie publiczne obiektu w zestawie Twoje dostosowania, który spełnia określone wymagania. Aby uzyskać więcej informacji, zobacz [buforowanie danych](../vsto/caching-data.md).|Wszystkie dane XML.|  
|Ma dostęp do danych bez uruchamiania aplikacji Microsoft Office?|Tak, przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Tak, korzystając z klas w <xref:System.IO.Packaging> przestrzeni nazw, lub za pomocą Otwórz SDK formatu XML.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  