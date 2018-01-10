---
title: 'Porady: Tworzenie dokumentu XML na podstawie schematu XSD | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 63ce40fb765d3aab4cb91ebff8a3552f69d92586
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2018
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Porady: Tworzenie dokumentu XML na podstawie schematu XSD
**Generowanie XML próbki** funkcja generuje przykładowy plik XML na podstawie Twojego pliku schematu XML (XSD).  
  
 Tej opcji można użyć w następujących scenariuszach:  
  
-   Aby zrozumieć użycie różne konstrukcje w schemat.  
  
-   Aby upewnić się, że schemat wykonuje co ma na celu.  
  
**Generowanie XML próbki** funkcja jest dostępna tylko na elementy globalne i wymaga prawidłowego zestawu schematu XML.  
  
Ta funkcja generuje zwykle ważnych dokumentów XML. Jednak jeśli schemat zawiera jeden lub więcej z następujących czynności, próbki mogą być nieprawidłowe:  
  
-   `xs:key`, `xs:keyref`, I `xs:unique` ograniczenia tożsamości.  
  
-   `xs:pattern`aspekty.  
  
-   Wyliczenia `xs:QName` typu.  
  
-   `xs:ENTITY`, `xs:ENTITIES`, i `xs:NOTATION` typów.  
  
Ponadto należy pamiętać, że `xs:base64Binary` zawartość zostanie wygenerowany tylko wtedy, gdy występują wyliczenia w schematu dla tego typu.  
  
### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Aby wygenerować wystąpienia dokumentu XML na podstawie pliku XSD  
  
1.  Postępuj zgodnie z instrukcjami [porady: tworzenie i edytowanie pliku schematu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  W [Eksploratora schematu XML](../xml-tools/xml-schema-explorer.md), kliknij prawym przyciskiem myszy `PurchaseOrder` element globalny. Wybierz **Generowanie przykładowy kod XML**.  
  
     Po wybraniu tej opcji, zostanie wygenerowany plik PurchaseOrder.xml o następującej treści XML próbki i będzie otwarty w edytorze XML:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Praca z danymi XML](../xml-tools/working-with-xml-data.md)