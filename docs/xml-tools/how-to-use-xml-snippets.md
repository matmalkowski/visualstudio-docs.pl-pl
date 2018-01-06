---
title: "Porady: wstawki XML za pomocą | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5d8c1d13263972462ef30e55a34c316f5dd0c7ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-xml-snippets"></a>Porady: Użyj fragmentów kodu XML
Można wywołać fragmentów kodu XML za pomocą następujących dwóch poleceń menu skrótów edytora XML. **Wstawić fragment** polecenia wstawia fragment kodu XML w bieżącej pozycji kursora. **z funkcji Otocz przez** polecenia opakowuje fragment kodu XML wokół zaznaczonego tekstu. Każdy fragment kodu XML wyznaczył fragment typów. Typy fragment określają, czy fragment kodu jest dostępna z **wstawić fragment** polecenia **z funkcji Otocz przez** polecenia lub obie.  
  
 Po dodaniu fragment kodu XML do edytora wszystkie pola edycji we fragmencie są wyróżnione kolorem żółtym i kursor znajduje się na pierwsze pole można edytować.  
  
## <a name="insert-snippet"></a>Wstawianie fragmentu kodu  
 W poniższych procedurach opisano sposób uzyskiwania dostępu do **wstawić fragment** polecenia.  
  
> [!NOTE]
>  **Wstawić fragment** polecenia jest również dostępny za pośrednictwem skrótu klawiaturowego (CTRL + K, a następnie klawisze CTRL + X).  
  
#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Do wstawienia fragmentów kodu z menu skrótów  
  
1.  Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.  
  
2.  Kliknij prawym przyciskiem myszy i wybierz **wstawić fragment**.  
  
     Zostanie wyświetlona lista dostępnych fragmentów kodu XML.  
  
3.  Wybierz fragment z listy za pomocą myszy lub wpisując nazwę fragmentu i naciskając klawisz TAB lub ENTER.  
  
#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Do wstawienia fragmentów kodu za pomocą IntelliSense menu  
  
1.  Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.  
  
2.  Z **Edytuj** menu wskaż **IntelliSense**, a następnie wybierz **wstawić fragment**.  
  
     Zostanie wyświetlona lista dostępnych fragmentów kodu XML.  
  
3.  Wybierz fragment z listy za pomocą myszy lub wpisując nazwę fragmentu i naciskając klawisz TAB lub ENTER.  
  
#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Do wstawienia fragmentów kodu za pomocą listy całe słowo IntelliSense  
  
1.  Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.  
  
2.  Rozpocznij wpisywanie fragment kodu XML, który chcesz dodać do pliku. Jeśli jest włączona funkcja automatycznego uzupełniania, zostanie wyświetlona lista całe słowo IntelliSense. Jeśli nie są wyświetlane, naciśnij klawisze CTRL + SPACJA, aby aktywować go.  
  
3.  Fragment kodu XML wybierz z listy całe słowo.  
  
4.  Naciśnij klawisz TAB, aby wywołać fragment kodu XML.  
  
> [!NOTE]
>  Mogą wystąpić przypadki, fragment kodu XML nie pobrać wywołania. Na przykład, jeśli podczas próby wstawienia `xs:complexType` element wewnątrz `xs:element` węzła, edytor nie generuje fragment kodu XML. Gdy `xs:complexType` element jest używany wewnątrz `xs:element` węzła, nie są wymagane atrybuty lub podelementów, dlatego edytor nie ma żadnych danych do wstawienia.  
  
#### <a name="to-insert-snippets-using-the-shortcut-name"></a>Do wstawienia fragmentów kodu przy użyciu nazwy skrótu  
  
1.  Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.  
  
2.  Typ `<` w okienku edytora.  
  
3.  Naciśnij klawisz ESC, aby zamknąć listę całe słowo IntelliSense.  
  
4.  Wpisz nazwę skrótów fragmentu, a następnie naciśnij klawisz TAB, aby wywołać fragment kodu XML.  
  
## <a name="surround-with"></a>Otocz przez  
 W poniższych procedurach opisano sposób uzyskiwania dostępu do **z funkcji Otocz przez** polecenia.  
  
> [!NOTE]
>  **z funkcji Otocz przez** polecenia jest również dostępny za pośrednictwem skrótu klawiaturowego (CTRL + K, a następnie klawisz CTRL + S).  
  
#### <a name="to-use-surround-with-from-the-context-menu"></a>Aby użyć przestrzennego z z menu kontekstowego  
  
1.  Zaznacz tekst, który należy ująć w edytorze XML.  
  
2.  Kliknij prawym przyciskiem myszy i wybierz **z funkcji Otocz przez**.  
  
     Zostanie wyświetlona lista dostępnych obudowy z fragmentów kodu XML.  
  
3.  Wybierz fragment z listy za pomocą myszy lub wpisując nazwę fragmentu i naciskając klawisz TAB lub ENTER.  
  
#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Aby użyć przestrzennego z menu Intellisense  
  
1.  Zaznacz tekst, który należy ująć w edytorze XML.  
  
2.  Z **Edytuj** menu wskaż **IntelliSense**, a następnie wybierz **z funkcji Otocz przez**.  
  
     Zostanie wyświetlona lista dostępnych obudowy z fragmentów kodu XML.  
  
3.  Wybierz fragment z listy za pomocą myszy lub wpisując nazwę fragmentu i naciskając klawisz TAB lub ENTER.  
  
## <a name="using-xml-snippets"></a>Przy użyciu fragmentów kodu XML  
 Po wybraniu fragment kodu XML tekst fragment kodu jest wprowadzana automatycznie na pozycji kursora. Wszystkie pola edycji we fragmencie są wyróżnione, a pierwsze pole edycji jest wybierana automatycznie. Aktualnie zaznaczone pole jest opakowany.  
  
 Po zaznaczeniu pola, możesz wpisać nową wartość dla pola. Naciśnięcie przycisku cykle kartę za pośrednictwem edytowalne pola fragmentu; Naciśnięcie klawisza SHIFT + TAB przełączanie po kolei je w odwrotnej kolejności. Kliknięcie pola umieszcza kursor w polu, a następnie dwukrotne kliknięcie pola zaznacza go. Jeśli pole zostanie wyróżniona, etykietkę narzędzia mogą być wyświetlane, oferty opis pola.  
  
 Można edytować jest tylko pierwsze wystąpienie danego pola. Gdy to pole jest podświetlona, podane są inne wystąpienia tego pola. Po zmianie wartości pola można edytować pola jest zmieniany wszędzie tam, gdzie jest używany we fragmencie.  
  
 Naciśnięcie klawisza ENTER lub ESC anuluje pola edycji i zwraca Edytor normalnie.  
  
 Domyślne kolory pola fragment kodu można edytować można zmienić, modyfikując ustawienie pola fragmentu kodu w **czcionki i kolory** okienku **opcji**okno dialogowe s. Aby uzyskać więcej informacji, zobacz [porady: zmiana czcionek i kolorów w edytorze](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Fragmentów kodu XML](../xml-tools/xml-snippets.md)   
 [Porady: generowanie fragment kodu XML na podstawie schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)   
 [Instrukcje: Tworzenie fragmentów kodu XML](../xml-tools/how-to-create-xml-snippets.md)