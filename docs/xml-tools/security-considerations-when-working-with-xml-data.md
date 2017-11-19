---
title: "Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 46bd68bd4556c782ac8dc6e1664dafe0ce80f99e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="security-considerations-when-working-with-xml-data"></a>Zagadnienia dotyczące zabezpieczeń podczas pracy z danych XML
W tym temacie omówiono problemy z zabezpieczeniami, które należy znać podczas pracy z edytora XML lub debuger XSLT.  
  
## <a name="xml-editor"></a>Edytor XML  
 Edytor XML jest oparta na Edytor tekstu Visual Studio. Opiera się na <xref:System.Xml> i <xref:System.Xml.Xsl> klasy do obsługi wielu procesów XML.  
  
-   Przekształcenia XSLT są wykonywane w nowej domenie aplikacji. Przekształcenia XSLT są *piaskownicy*; oznacza to, że zasady zabezpieczeń dostępu kodu komputera służy do określania ograniczone uprawnienia oparte na którym znajduje się arkusz stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej ma najbardziej ograniczone uprawnienia, podczas gdy arkusze stylów skopiowany na dysk twardy, uruchom z pełnego zaufania.  
  
-   <xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest używana do kompilowania XSLT na język pośredni firmy Microsoft, aby zwiększyć wydajność podczas wykonywania.  
  
-   Schematy wskazujące zewnętrznej lokalizacji w pliku wykazu są automatycznie pobierane po pierwszym załadowaniu edytora XML. <xref:System.Xml.Schema.XmlSchemaSet> Klasa jest używana do kompilowania schematów. Plik katalogu, który jest dostarczany z edytora XML nie ma linki do dowolnego schematów zewnętrznych. Użytkownik musi jawnie dodać odwołanie do schematu zewnętrznych przed edytora XML pobieranie pliku schematu. Pobieranie HTTP można wyłączyć za pomocą **różne opcje narzędzia** strony edytora XML.  
  
-   Edytor XML używa <xref:System.Net> klas, aby pobrać schematów  
  
## <a name="xslt-debugger"></a>Debuger XSLT  
 Debuger XSLT korzysta z aparatu debugowania zarządzanego programu Visual Studio i klas z <xref:System.Xml> i <xref:System.Xml.Xsl> przestrzeni nazw.  
  
-   Debuger XSLT działa każdy przekształcenie XSLT w domenie aplikacji piaskownicy. Zasady zabezpieczeń dostępu kodu komputera służy do określenia ograniczone uprawnienia oparte na którym znajduje się arkusz stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej ma najbardziej ograniczone uprawnienia, podczas gdy arkusze stylów skopiowany na dysk twardy, uruchom z pełnego zaufania.  
  
-   Arkusz stylów XSLT jest skompilowana przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
-   Ewaluator wyrażeń XSLT jest ładowany przez aparat debugowania zarządzanego. Aparat debugowania zarządzanego przyjęto założenie, że cały kod jest uruchamiany z komputera lokalnego użytkownika. W związku z tym <xref:System.Xml.Xsl.XslCompiledTransform> klasy pobiera plik XSLT do użytkownika komputera lokalnego. Możliwość, że podwyższenie poziomu w uprawnień do wykonywania może wystąpić skuteczność została osłabiona, wykonując wszystkie przekształcenia XSLT w nowej domenie aplikacji z ograniczonymi uprawnieniami  
  
## <a name="see-also"></a>Zobacz też  
 [Domeny aplikacji](/dotnet/framework/app-domains/application-domains)  