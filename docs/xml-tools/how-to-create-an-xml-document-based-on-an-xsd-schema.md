---
title: 'Porady: Tworzenie dokumentu XML na podstawie schematu XSD'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d3da2e6b5b0c9ea2701524c0fb2fde1e1313687
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Porady: Tworzenie dokumentu XML na podstawie schematu XSD

**Generowanie XML próbki** funkcja generuje przykładowy plik XML na podstawie Twojego pliku schematu XML (XSD).

 Tej opcji można użyć w następujących scenariuszach:

-   Aby zrozumieć użycie różne konstrukcje w schemat.

-   Aby upewnić się, że schemat wykonuje co ma na celu.

**Generowanie XML próbki** funkcja jest dostępna tylko na elementy globalne i wymaga prawidłowego zestawu schematu XML.

Ta funkcja generuje zwykle ważnych dokumentów XML. Jednak jeśli schemat zawiera jeden lub więcej z następujących czynności, próbki mogą być nieprawidłowe:

-   `xs:key`, `xs:keyref`, I `xs:unique` ograniczenia tożsamości.

-   `xs:pattern` aspekty.

-   Wyliczenia `xs:QName` typu.

-   `xs:ENTITY`, `xs:ENTITIES`, i `xs:NOTATION` typów.

Ponadto należy pamiętać, że `xs:base64Binary` zawartość zostanie wygenerowany tylko wtedy, gdy występują wyliczenia w schematu dla tego typu.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Aby wygenerować wystąpienia dokumentu XML na podstawie pliku XSD

1.  Postępuj zgodnie z instrukcjami [porady: tworzenie i edytowanie pliku schematu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  W [Eksploratora schematu XML](../xml-tools/xml-schema-explorer.md), kliknij prawym przyciskiem myszy `PurchaseOrder` element globalny. Wybierz **Generowanie przykładowy kod XML**.

     Po wybraniu tej opcji, PurchaseOrder. *xml* pliku o następującej treści XML próbki zostanie wygenerowany i otwarty w edytorze XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```

## <a name="see-also"></a>Zobacz także

- [Praca z danych XML](../xml-tools/working-with-xml-data.md)