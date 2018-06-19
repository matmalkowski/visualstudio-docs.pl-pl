---
title: Tworzenie nowego testu usług sieci Web w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 2ae66ff032b3f43f80f8c00b12e2d344bba298b9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970707"
---
# <a name="how-to-create-a-web-service-test"></a>Porady: tworzenie nowego testu usług sieci Web

Testy wydajności sieci Web mogą służyć do testowania usług sieci Web. Za pomocą **Wstaw żądanie** i **Wstaw żądanie usługi sieci Web** opcje, można dostosować poszczególnych żądań w **edytora testów wydajności sieci Web** można znaleźć w sieci Web strony usługi. Zazwyczaj tych stron nie wyświetla się w aplikacji sieci Web. W związku z tym należy dostosować żądanie, aby uzyskać do nich dostęp.

W procedurach poniżej jest wykorzystywana usługa sieci Web zawarta w pakiecie startowym Commerce Starter Kit. Możesz pobrać go z [ASP.NET Commerce Starter Kit](http://go.microsoft.com/fwlink/?LinkId=181469).

 **Wymagania**

-   Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Aby przetestować usługę sieci Web

1.  Tworzenie nowego testu wydajności sieci Web. Zaraz po otwarciu przeglądarki wybierz **zatrzymać**.

2.  W **edytora testów wydajności sieci Web**, kliknij prawym przyciskiem myszy testu wydajności sieci Web i wybierz **Dodaj żądanie usługi sieci Web**.

3.  W **adres Url** właściwości nowe żądanie, wpisz nazwę usługi sieci Web, takich jak **http://localhost/storecsvs/InstantOrder.asmx**.

4.  Otwórz oddzielne sesję przeglądarki, a następnie wpisz adres URL strony .asmx w **adres** paska narzędzi. Wybierz metodę, którą chcesz przetestować i uważnie przeczytaj komunikat protokołu SOAP. Zawiera on element `SOAPAction`.

5.  W **edytora testów wydajności sieci Web**, kliknij prawym przyciskiem myszy żądanie i wybierz **Dodawanie nagłówka** Aby dodać nowy nagłówek. W **nazwa** właściwości, typ `SOAPAction`. W **wartość** właściwości, wpisz wartość, która pojawi się w `SOAPAction`, takich jak `"http://tempuri.org/CheckStatus"`.

6.  Rozwiń węzeł adresu URL w edytorze, wybierz **ciągów tekstowych** węzeł i w **typu zawartości** właściwości wprowadź wartość `text/xml`.

7.  Wróć do przeglądarki z kroku 4, na stronie z opisem usługi sieci Web zaznacz fragment XML żądania protokołu SOAP i skopiuj go do schowka.

8.  Zawartość XML przypomina poniższy przykład:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. Wróć do **edytora testów wydajności sieci Web** , a następnie wybierz wielokropek (...) w **ciągów tekstowych** właściwości. Wklej zawartość schowka do właściwości.

10. Aby test kończył się pomyślnie, zamień wszystkie wartości wieloznaczne w kodzie XML prawidłowymi wartościami. W poprzednim przykładzie należy zamienić dwa wystąpienia wartości `string` i jedno wartości `int`. Ta operacja usługi sieci Web zostanie wykonana tylko pod warunkiem, że istnieje zarejestrowany użytkownik, który złożył zamówienie.

11. Kliknij prawym przyciskiem myszy na żądanie usługi sieci Web i wybierz **Dodaj parametr QueryString adresu URL**.

12. Przypisz parametrowi ciągu zapytania nazwę i wartość. W poprzednim przykładzie nazwą jest `op` i wartość jest `CheckStatus`. W ten sposób została zidentyfikowana operacja usługi sieci Web, która ma zostać wykonana.

    > [!NOTE]
    > Powiązanie danych można użyć w treści protokołu SOAP zastąpienia wartości symbolu zastępczego z wartościami danych powiązany za pomocą `{{DataSourceName.TableName.ColumnName}}` składni.

13. Uruchom test. W górnym okienku podglądu wyników testu wydajności sieci Web zaznacz żądanie usługi sieci Web. W dolnym okienku kliknij kartę Przeglądarka sieci Web. Zostanie wyświetlony kod XML zwracany przez usługę sieci Web oraz wyniki wszelkich operacji.

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)