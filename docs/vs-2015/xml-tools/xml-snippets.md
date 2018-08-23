---
title: Fragmentów kodu XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bae360d1aea43006138397b3bed2857a2b1dad59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681115"
---
# <a name="xml-snippets"></a>Fragmenty kodu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [fragmentów kodu XML](https://docs.microsoft.com/visualstudio/xml-tools/xml-snippets).  
  
  
Edytor XML oferuje funkcję o nazwie *fragmentów kodu XML*, który pozwala szybciej tworzyć pliki XML. Można ponownie użyć fragmentów kodu XML, wstawiając je do plików. Można również wygenerować danych XML na podstawie schematu języka (XSD) definicji schematu XML.  
  
## <a name="reusable-xml-snippets"></a>Fragmentów kodu XML do ponownego wykorzystania  
 Edytor XML zawiera wiele fragmentów kodu, które obejmują niektóre typowe zadania. Dzięki temu można łatwiej tworzyć pliki XML. Na przykład jeśli zostały tworzenia schematu XML, za pomocą "Złożonych typów sekwencji Element" i "Prosty Element Type" fragmenty wstawia następujący tekst XML do pliku. Następnie należy zmienić `name` wartości do własnych potrzeb.  
  
```  
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
  
 Fragmenty kodu można wstawić na dwa sposoby. **Wstaw fragment kodu** polecenia wstawia fragment kodu XML w położeniu kursora. **Otocz** polecenia opakowuje fragment kodu XML wokół zaznaczonego tekstu. Oba polecenia są dostępne albo z **IntelliSense** podmenu w obszarze **Edytuj** menu lub z menu skrótów edytora.  
  
 Aby uzyskać więcej informacji, zobacz [porady: użycie fragmentów kodu z XML](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Wygenerowany schemat XML fragmentów kodu  
 Edytor XML ma również możliwość Generowanie fragmentu kodu XML na podstawie schematu XML. Ta funkcja umożliwia wypełnić element z elementów XML wygenerowany na podstawie informacji o schemacie dla tego elementu.  
  
 Aby uzyskać więcej informacji, zobacz [porady: generowanie fragmentu kodu z XML schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Tworzenie nowych fragmentów kodu XML  
 Oprócz fragmenty kodu, które są dołączone [!INCLUDE[msCoName](../includes/msconame-md.md)] programu Visual Studio domyślnie można również tworzyć i używać własnych fragmentów kodu XML.  
  
 Aby uzyskać więcej informacji, zobacz [porady: tworzenie fragmentów kodu XML](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)



