---
title: Fragmenty XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47410a4f87d6e8afd1af6f41583261c101883562
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="xml-snippets"></a>Fragmentów kodu XML
Edytor XML oferuje funkcję, *fragmentów kodu XML*, co umożliwia szybkie tworzenie plików XML. Można ponownie użyć fragmentów kodu XML, wstawiając je do plików. Można również generować dane XML na podstawie schematu schematu XML definition language (XSD).  
  
## <a name="reusable-xml-snippets"></a>Fragmenty XML wielokrotnego użytku  
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
  
 Aby uzyskać więcej informacji, zobacz [porady: użycie fragmentów kodu XML](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Wstawki kodu programu wygenerować schematu XML  
 Edytor XML ma również możliwości, aby wygenerować fragment kodu XML na podstawie schematu XML. Ta funkcja pozwala wypełnić element z elementów XML generowane na podstawie informacji o schemacie dla tego elementu.  
  
 Aby uzyskać więcej informacji, zobacz [porady: generowanie fragment kodu z XML schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Tworzenie nowych fragmentów kodu XML  
 Oprócz fragmenty kodu, które są dołączone do [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] programu Visual Studio domyślnie można również tworzyć i używać własnych fragmentów kodu XML.  
  
 Aby uzyskać więcej informacji, zobacz [porady: tworzenie fragmentów kodu XML](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)