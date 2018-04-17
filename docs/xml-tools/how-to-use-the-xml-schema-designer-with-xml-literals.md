---
title: 'Porady: Użyj projektanta schematu XML z literałów XML | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 504b063ccbc9646755891fc0eea3647a5594b213
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Porady: Użyj projektanta schematu XML z literałów XML
W tym temacie opisano sposób wyświetlania schematu skojarzone z pliku XML literał w projektach Visual Basic.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>Aby utworzyć nowy projekt aplikacji konsoli języka Visual Basic  
  
1.  Uruchom program Visual Studio.  
  
2.  Z **pliku** menu, wybierz opcję **nowy**, a następnie wybierz **projektu**. **Nowy projekt** zostanie wyświetlone okno dialogowe. Dla **typy projektów**, wybierz pozycję **inne języki** , a następnie wybierz **Visual Basic**. Aby uzyskać **szablony**, wybierz aplikację konsoli. Następnie wpisz `XMLLiterals` w **nazwa** pola i lokalizację projektu w **lokalizacji** pola. Kliknij przycisk **OK**.  
  
     Tworzony jest nowy projektu zlecenie serwisowe. Projekt XMLLiterals zawiera jeden plik źródłowy języka Visual Basic, Module1.vb.  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Aby dodać istniejący plik XSD do projektu  
  
1.  Otwórz nowy tekst w pliku Notepad.Copy schematu XML przykładowego kodu z [schematu zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md) i wklej je do pliku.  
  
2.  Zapisz plik w określonej lokalizacji o nazwie PurchaseOrderSchema.xsd.  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nazwę projektu, zaznacz **Dodaj**, a następnie wybierz **istniejący element...** . **AddExisting elementu** zostanie wyświetlone okno dialogowe. Przejdź do pliku PurchaseOrderSchema.xsd, zaznacz go, a następnie kliknij przycisk **Dodaj**.  
  
     Projekt XMLLiterals zawiera teraz dwa pliki: Module1.vb i PurchaseOrderSchema.xsd.  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Aby dodać kod Visual Basic z pliku XML literału, na podstawie pliku XSD dołączony do projektu  
  
1.  Zastąp kod w pliku Module1.vb następujący kod:  
  
   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
   Module Module1  
       Sub Main()  
  
           Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                <ns:ShipTo country="US">  
                                    <ns:name>name1</ns:name>  
                                    <ns:street>street1</ns:street>  
                                    <ns:city>city1</ns:city>  
                                    <ns:state>state1</ns:state>  
                                    <ns:zip>1</ns:zip>  
                                </ns:ShipTo>  
                                <ns:BillTo country="US">  
                                    <ns:name>name1</ns:name>  
                                    <ns:street>street1</ns:street>  
                                    <ns:city>city1</ns:city>  
                                    <ns:state>state1</ns:state>  
                                    <ns:zip>1</ns:zip>  
                                </ns:BillTo>  
                            </ns:PurchaseOrder>  
  
       End Sub  
   End Module  
   ```
  
2.  Kliknij prawym przyciskiem myszy dowolnego węzła XML w literał XML lub importu przestrzeni nazw XML, a następnie wybierz **Pokaż w Eksploratorze schematu**.  
  
     Eksploratora schematu XML jest wyświetlany obok pliku Visual Basic, który ma literału assotiated ze schematem XML XML ustawić.