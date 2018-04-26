---
title: 'Wskazówki: Używanie XSLT IntelliSense'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3240868ce8f749bf97a12054aac4760018c71d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-using-xslt-intellisense"></a>Wskazówki: Używanie XSLT IntelliSense

W tym przewodniku pokazano, jak technologię XSLT IntelliSense do automatycznego zakończenia wartości niektórych atrybutów.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Aby użyć funkcji IntelliSense w atrybut name elementu xsl: z param i XSL: call-elementów szablonu

1.  Utwórz nowy plik XSLT i skopiuj poniższy kod:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2.  Wstaw kursor po `<xsl:template name="msg23" match="msg23">` i naciśnij klawisz ENTER. Zacznij pisać następujące `xsl:call-template` elementu:

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     Lista nazw szablonu jest wyświetlana w `name=""` atrybutu `xsl:call-template` elementu podczas pisania.

3.  Wstaw kursor po `<xsl:call-template name="localized-message">` i naciśnij klawisz ENTER. Zacznij pisać następujące `xsl:with-param` elementu:

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     Lista nazw parametrów jest wyświetlana w `name=""` atrybutu `xsl:with-param` elementu.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Do używania funkcji IntelliSense w atrybucie tryb xsl: zastosować szablony elementu

1.  Utwórz nowy plik XSLT i skopiuj poniższy kod:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2.  Wstaw kursor po `<xsl:apply-templates select="phone" />` i naciśnij klawisz ENTER. Zacznij pisać następujące `xsl: apply-templates` elementu:

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     Lista trybów szablonu jest wyświetlana w `mode=""` atrybutu `xsl:apply-templates` elementu.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Używać funkcji IntelliSense w atrybuty arkusza stylów prefiks i prefiksu wynik xsl:namespace — w elemencie aliasu

1.  Utwórz nowy plik XSLT i skopiuj poniższy kod:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2.  Wstaw kursor po `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` i naciśnij klawisz ENTER. Zacznij pisać następujące `xsl:namespace-alias` elementu:

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Zwróć uwagę, jak Lista prefiksów znajdowały się w `stylesheet-prefix` i `result-prefix` atrybuty `xsl:namespace-alias` elementu.

## <a name="see-also"></a>Zobacz także

- [Funkcje IntelliSense w edytorze XML](../xml-tools/xml-editor-intellisense-features.md)