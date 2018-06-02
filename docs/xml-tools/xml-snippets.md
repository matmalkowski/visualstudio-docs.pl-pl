---
title: Fragmenty kodu XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07ddb1dd64e5d972c23a032cb1eb752515d92ab6
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693854"
---
# <a name="xml-snippets"></a>Fragmentów kodu XML

Edytor XML oferuje funkcję, *fragmentów kodu XML*, co umożliwia szybkie tworzenie plików XML. Można ponownie użyć fragmentów kodu XML, wstawiając je do plików. Można również generować dane XML na podstawie schematu schematu XML definition language (XSD).

## <a name="reusable-xml-snippets"></a>Wielokrotnego użytku fragmentów kodu XML

Edytor XML zawiera wiele fragmentów, które obejmują kilka typowych zadań. Dzięki temu można łatwiej tworzenia plików XML. Na przykład jeśli zostały tworzenia schematu XML przy użyciu "Złożonego typu sekwencji elementu" i wstawki "Proste elementu typu" wstawia następujący tekst XML do pliku. Następnie należy zmienić `name` wartości w zależności od potrzeb.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

 Możesz wstawić wstawki na dwa sposoby. **Wstawić fragment** polecenia wstawia fragment kodu XML w bieżącej pozycji kursora. **z funkcji Otocz przez** polecenia opakowuje fragment kodu XML wokół zaznaczonego tekstu. Albo oba polecenia są dostępne z **IntelliSense** podmenu w **Edytuj** menu lub menu skrótów edytora.

 Aby uzyskać więcej informacji, zobacz [porady: wstawki XML użyj](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Schemat wygenerowany fragmentów kodu XML
 Edytor XML ma również możliwości, aby wygenerować fragment kodu XML na podstawie schematu XML. Ta funkcja pozwala wypełnić element z elementów XML generowane na podstawie informacji o schemacie dla tego elementu.

 Aby uzyskać więcej informacji, zobacz [porady: generowanie fragment kodu XML na podstawie schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Tworzenie nowych fragmentów kodu XML
 Oprócz fragmenty kodu, które są dołączone do [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] programu Visual Studio domyślnie można również tworzyć i używać własnych fragmentów kodu XML.

 Aby uzyskać więcej informacji, zobacz [porady: tworzenie XML wstawki](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)