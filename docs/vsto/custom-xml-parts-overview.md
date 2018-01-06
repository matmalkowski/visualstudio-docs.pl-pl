---
title: "Niestandardowy plik XML części omówienie | Dokumentacja firmy Microsoft"
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
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 735660c3af1c0a8792a35981788b70f4a79d55b1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="custom-xml-parts-overview"></a>Niestandardowe części XML ― Omówienie
  Dane XML można osadzić w dokumentach niektórych aplikacji pakietu Microsoft Office. Po osadzeniu danych XML w dokumencie dane o nazwie *niestandardowym elementem XML*.  
  
 Można tworzyć i modyfikować niestandardowe elementy XML w dokumencie przy użyciu dodatku VSTO lub poziomie dokumentu w środowisku Visual Studio. Nie trzeba uruchomić aplikację Microsoft Office do tworzenia i modyfikowania niestandardowe elementy XML.  
  
 **Dotyczy:** informacje w tym temacie dotyczą projektów na poziomie dokumentu i projektów dodatku VSTO dla programu Excel, PowerPoint i Word. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Program Visual Studio umożliwia także do buforowania danych obiektów w dostosowaniach na poziomie dokumentu. Ta funkcja jest inna niż niestandardowe elementy XML, chociaż istnieją pewne podobieństwa. Aby uzyskać więcej informacji, zobacz [buforowane dane w dostosowaniach na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understanding-custom-xml-parts"></a>Opis niestandardowych części XML  
 Niestandardowe elementy XML wprowadzono w programie Microsoft Office system 2007, wraz z otwartych formatów XML. Te formaty to nowe formaty plików XML dla programu Excel, PowerPoint i Word (np. xlsx, pptx i .docx). Dokumenty w tych formatach składają się z plikami XML (o nazwie *elementy XML*) który są zorganizowane w folderach w archiwum ZIP. Większość elementy XML są wbudowane części, które pomogą Ci określić struktury i stanu dokumentu. Jednak dokumenty mogą również zawierać niestandardowe elementy XML, których można używać do przechowywania danych dowolnego XML w dokumentach.  
  
 Formaty plików XML umożliwiają aplikacjom Praca z dokumentami w sposób, w którym nie są możliwe w starszych formatach pliku binarnego (na przykład xls, ppt i doc). Każda aplikacja, która może odczytywać archiwum ZIP można zbadać i modyfikować zawartość dokumentów, nawet jeśli nie zainstalowano programu Microsoft Office.  
  
 Aby uzyskać więcej informacji na temat struktury Open XML i niestandardowe elementy XML zobacz następujące artykuły:  
  
-   [Wprowadzenie do formatów pakietu Office (2007) Open XML](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Porady: manipulowanie dokumentów formatów Open XML](http://msdn.microsoft.com/en-us/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Wskazówki: Word 2007 XML formatu](http://msdn.microsoft.com/en-us/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Tworzenie dokumentów programu Word 2007, przy użyciu Open XML formatów](http://msdn.microsoft.com/en-us/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Program Excel, Word i PowerPoint również włączyć użycia niestandardowe elementy XML w dokumentach, które są zapisywane w formatach plików binarnych. Jednak jeśli dokument jest zapisywany w formacie binarnym, nie dodaje lub modyfikuje niestandardowe elementy XML bez uruchamiania aplikacji Microsoft Office.  
  
## <a name="creating-and-modifying-custom-xml-parts"></a>Tworzenie i modyfikowanie niestandardowych części XML  
 Można utworzyć lub zmodyfikować niestandardowe elementy XML w przypadku, gdy dokument jest otwarty w aplikacji pakietu Office, lub gdy dokument zostanie zamknięty, nawet jeśli nie zainstalowano programu Microsoft Office.  
  
### <a name="modifying-xml-parts-while-the-office-application-is-running"></a>Modyfikowanie elementy XML w uruchomionej aplikacji pakietu Office  
 Niestandardowe elementy XML mogą współpracować przy użyciu dostosowania poziomie dokumentu lub dodatku VSTO. Jeśli używasz dostosowania poziomie dokumentu można zwykle współdziałają z niestandardowe elementy XML, znajdujących się w dokumencie dostosowane. Jeśli używasz dodatku VSTO, można utworzyć lub zmodyfikować niestandardowe elementy XML w dowolnych dokumentów, która jest otwarta w aplikacji.  
  
 Aby utworzyć z niestandardowym elementem XML przy użyciu programu Visual Studio, Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> do <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w dokumencie. Więcej informacji znajduje się w następujących tematach:  
  
-   [Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentów](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modifying-xml-parts-without-starting-the-office-application"></a>Modyfikowanie elementy XML bez uruchamiania aplikacji pakietu Office  
 Można dodawać lub modyfikować z niestandardowym elementem XML bez konieczności uruchamiania programu Excel, PowerPoint lub słowa. Jest to przydatne, jeśli chcesz pracować z danymi XML w dokumencie na komputerze, który nie ma zainstalowany, takim jak serwer aplikacji Microsoft Office.  
  
 Aby dodać z niestandardowym elementem XML bez konieczności uruchamiania programu Microsoft Office, należy użyć klasy w zestawie SDK Open XML. Te klasy mają na celu zapewnienia dostępu do zawartości Open XML, która jest specyficzna dla dokumentów pakietu Office. Na przykład aby dodać z niestandardowym elementem XML do skoroszytu programu Excel, możesz użyć [AddNewPart\<T >](http://msdn.microsoft.com/en-us/47c348c0-77ab-a504-5097-bcd6a213921a) metody [WorkbookPart](http://msdn.microsoft.com/en-us/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2) obiektu. Aby uzyskać więcej informacji, zobacz [Open XML SDK 2.0](http://msdn.microsoft.com/en-us/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## <a name="binding-custom-xml-parts-to-word-content-controls"></a>Powiązanie z kontrolkami zawartości programu Word niestandardowych części XML  
 Formanty zawartości można powiązać w rozwiązaniu programu Word do elementów z niestandardowym elementem XML. Gdy zawartość formantu jest powiązana z niestandardowym elementem XML, dane w niestandardowym elementem XML są wyświetlane w interfejsie użytkownika (UI) zawartości formantu. Jeśli użytkownik edytuje tekst w formancie, jest automatycznie aktualizowany odpowiadającego mu elementu XML. Podobnie zmiana wartości elementów w niestandardowe elementy XML formantów zawartości, które są powiązane z elementów XML wyświetlanie nowych danych. Aby uzyskać więcej informacji, zobacz [formantów zawartości](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Schematy XML i danych na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Porady: Dodawanie niestandardowych części XML na poziomie dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Porady: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Formanty zawartości](../vsto/content-controls.md)   
 [Przewodnik: Powiązywanie kontrolek zawartości do niestandardowych części XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  