---
title: 'Porady: Użyj projektanta schematu XML z literałów XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 589bfa54a0ba1a7efb2964cf5b74446ca9ffe10d
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Porady: Użyj projektanta schematu XML z literałów XML

W tym temacie opisano sposób wyświetlania schematu skojarzone z pliku XML literał w projektach Visual Basic.

## <a name="to-create-a-new-visual-basic-console-application-project"></a>Aby utworzyć nowy projekt aplikacji konsoli języka Visual Basic

1.  Uruchom program Visual Studio.

2.  Z **pliku** menu, wybierz opcję **nowy**, a następnie wybierz **projektu**. **Nowy projekt** zostanie wyświetlone okno dialogowe. Dla **typy projektów**, wybierz pozycję **inne języki** , a następnie wybierz **Visual Basic**. Aby uzyskać **szablony**, wybierz aplikację konsoli. Następnie wpisz `XMLLiterals` w **nazwa** pola i lokalizację projektu w **lokalizacji** pola. Kliknij przycisk **OK**.

     Tworzony jest nowy projektu zlecenie serwisowe. Projekt XMLLiterals zawiera jeden plik źródłowy języka Visual Basic, *Module1.vb*.

## <a name="to-add-an-existing-xsd-file-to-the-project"></a>Aby dodać istniejący plik XSD do projektu

1.  Otwórz nowy plik tekstowy w Notatniku. Skopiuj schematu XML przykładowego kodu z [schematu zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md) i wklej je do pliku.

2.  Zapisz plik w określonej lokalizacji o nazwie *PurchaseOrderSchema.xsd*.

3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nazwę projektu, zaznacz **Dodaj**, a następnie wybierz **istniejący element**. **AddExisting elementu** zostanie wyświetlone okno dialogowe. Przejdź do *PurchaseOrderSchema.xsd* plików, wybierz go, a następnie kliknij przycisk **Dodaj**.

     Projekt XMLLiterals zawiera teraz dwa pliki: *Module1.vb* i *PurchaseOrderSchema.xsd*.

## <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Aby dodać kod Visual Basic z pliku XML literału, na podstawie pliku XSD dołączony do projektu

1.  Zastąp kod w *Module1.vb* pliku następującym kodem:

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

     **Eksploratora schematu XML** jest wyświetlany obok pliku Visual Basic, który ma literał XML skojarzone z zestawu schematów XML.